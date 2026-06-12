---
title: "Anyone got MIR working in raring?"
date: 2013-03-13
forum: Ubuntu Development Version
---

### Post by DisappearingOak on 2013-03-13
I added MIR staging ppa, and installed mir package. 
Now I switched to a different virtual terminal through Ctrl+ALT+F2 / F3, etc. Then I logged in and ran $ mir
Doing that, all I get is a black screen. If I try switching to different terminal, it doesn't work, I think that's something to do with how mir works, I assume. Only black screen. Num Lock works. Have to reset machine.
Mine is Radeon HD 4250 on AMD 880G.

Is that how Mir is supposed to be ran or something else, because I can't find instructions. Thanks.

---

### Post by dino99 on 2013-03-13
you might know thats a pre-pre-pre-pre-alpha with a non finite design; so what do you expect exactly ?

---

### Post by grahammechanical on 2013-03-13
some of us are also looking for instructions. This is about all that has been found so far. Well, it is all that I know. In the tty (Ctrl+Alt+F1 - in my case) try these three commands

```
(sleep 5; mir_demo_client) & mir; kill$!
```
```
(sleep 5; mir_demo_unaccelerated) & mir; kill$!
```
```
(sleep 5; mir_demo_accelerated) & mir; kill$!
```

What results do you get? To stop the demonstration press Ctrl+C. We get something with the accelerated demo but not much else with the other two demos. Ventrical worked out the 'sleep 5' = delay in running the demo. The lower the number the quicker the demo starts. The higher the number the longer the demo takes to start. So, wait a bit to see what happens before concluding that something is broken.

Sorry, I have nothing else to add. I have also installed the PPA for the Ubuntu Touch apps. But I cannot run any of the apps due to missing libraries that are not yet in the repository. That seems to be the state of things at the moment.

Regards.

Edit: Sorry. My mistake. That is why I don't like coding. Too large a risk for mistyping on my part. The argument should be enclosed in brackets. I have now corrected my error.

---

### Post by DisappearingOak on 2013-03-13
Syntax error :)  I'm assuming the ")" wasn't meant to be there. The commands printed the startup lines about libEGL and then the black screen issue again, on all three commands. Had to ALT-Ctrl-Del to restart the comp. I guess mir won't work on my hardware yet. Guess I'll have to wait to see the demo. /searches youtube

---

### Post by ventrical on 2013-03-13
> **DisappearingOak said:**
> Syntax error :)  I'm assuming the ")" wasn't meant to be there. The commands printed the startup lines about libEGL and then the black screen issue again, on all three commands. Had to ALT-Ctrl-Del to restart the comp. I guess mir won't work on my hardware yet. Guess I'll have to wait to see the demo. /searches youtube

Try the below code:

(sleep 5; mir_demo_client_accelerated) & mir ; kill $!

The brackets are needed.  It should work on your hardware. I have it working on ATi, Intel and Nvidia graphics.

---

### Post by grahammechanical on 2013-03-13
I have corrected my typing error. There should be an ( at the start and an ) at the end of the command to run. See corrected commands. Sorry.

---

### Post by ventrical on 2013-03-13
> **grahammechanical said:**
> some of us are also looking for instructions. This is about all that has been found so far. Well, it is all that I know. In the tty (Ctrl+Alt+F1 - in my case) try these three commands

```
(sleep 5; mir_demo_client) & mir; kill$!
```
```
(sleep 5; mir_demo_unaccelerated) & mir; kill$!
```
```
(sleep 5; mir_demo_accelerated) & mir; kill$!
```

What results do you get? To stop the demonstration press Ctrl+C. We get something with the accelerated demo but not much else with the other two demos. Ventrical worked out the 'sleep 5' = delay in running the demo. The lower the number the quicker the demo starts. The higher the number the longer the demo takes to start. So, wait a bit to see what happens before concluding that something is broken.

Sorry, I have nothing else to add. I have also installed the PPA for the Ubuntu Touch apps. But I cannot run any of the apps due to missing libraries that are not yet in the repository. That seems to be the state of things at the moment.

Regards.

Edit: Sorry. My mistake. That is why I don't like coding. Too large a risk for mistyping on my part. The argument should be enclosed in brackets. I have now corrected my error.

 I e-mailed Thomas Voss in launchpad if there were more demo material and code that we could experiment with and I am awaiting a reply. (which may be for along period of time ) :)

 I searched quite a bit .. mabey not enough but can't find any add-ons to the hacking file at launchpad.

  I have done some of my own experiements  based on the assumption that using the code:

```

& mir

```

invokes the MIR server .. so  one may be albe to load stuff or try to load stuff into it. I have tried gedit, gksu gedit, lightdm etc.. with varying results. I am not worried about borking installs because I have 4 machines commited to it.

 I tired the command:

```

startx mir

```

and got a white box at the top left hand corner for about a second, then blackspace and out with CTRL+c. I am not advising anyone to experiment in this way if you are not willing to bust, fry or otherwise bork your system. I have only borked one install so far and that is when I tried the code:

```


(sleep 5; ubuntu-desktop) & mir ; kill $!


```

---

### Post by ventrical on 2013-03-13
I am also trying to find out what happened to the conventional .xinitrc file  that follows startx so I can try and build a script to run with MIR init but tlooks like Ubuntu does not work off of this process as conventional Linux does?

---

### Post by zika on 2013-03-13
> **ventrical said:**
> I am also trying to find out what happened to the conventional .xinitrc file  that follows startx so I can try and build a script to run with MIR init but tlooks like Ubuntu does not work off of this process as conventional Linux does?.xinitrc (or .Xsession, You pick which one You want use) works nicely... Just You have to know several rules... They are easily obtained...
My current (testing, mess but useful to learn how (or how not to) use it:```
:~$ cat .xinitrc#/usr/bin/xcompmgr &
/usr/bin/gnome-settings-daemon &
#/usr/bin/glipper &
#/usr/bin/indicator-weather &
/usr/bin/xset r rate 250 40 &
/usr/bin/setxkbmap -option lv3:ralt_switch,grp:sclk_toggle,grp_led:scroll,eurosign:5 rs,rs -variant latin, altwin:swap_lalt__lwin, caps:super &
/usr/bin/pulseaudio --daemonize &
#/usr/bin/pacmd set-source-volume alsa_output.usb-Burr-Brown_from_TI_USB_Audio_DAC-00-DAC.iec958-stereo.monitor 65536 &
#/usr/bin/awsetbg -f /home/zika/black_2048_1152.jpg &
#/usr/bin/awsetbg -f /home/zika/Pictures/BlackSnake.jpg &
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/awesome
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
#/usr/bin/ck-launch-session /usr/bin/gnome-session-fallback
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session-fallback
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-shell
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/dwm
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/fvwm
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/spectrwm
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/unity
#exec /usr/bin/ck-launch-session /usr/bin/gnome-session --session=gnome-fallback-compiz
#exec /usr/bin/ck-launch-session /usr/bin/gnome-session --session=gnome-fallback
#exec /usr/bin/ck-launch-session /usr/bin/awesome
exec /usr/bin/ck-launch-session /usr/bin/gnome-shell
#exec /usr/bin/ck-launch-session /usr/bin/unity
#exec /usr/bin/ck-launch-session /usr/bin/weston --fullscreen --backend=drm-backend.so
```

---

### Post by DisappearingOak on 2013-03-13
Edit sorry, I just read ventrical's corrected command. let me try that.
black screen again but I can quit it with Ctrl+C.
I get mir_demo_client_accelerated: command not found.
libEGL warning: failed to load /../egl_gallium.so (libllvmradeon9.2.0.so Could not open shared object No such file or directory)

I got the command not found on grahams three commands also, even after the correction.

---

### Post by ventrical on 2013-03-13
> **DisappearingOak said:**
> Edit sorry, I just read ventrical's corrected command. let me try that.

Did you copy and paste or did you enter manually because there are spaces between certain arguments..

(sleep 5; mir_demo_accelerated)<space>&<space>mir<space>;<space>kill<space>$!

Either that or your hardware is too new.

Do you have all of these files?

---

### Post by ventrical on 2013-03-13
> **zika said:**
> .xinitrc (or .Xsession, You pick which one You want use) works nicely... Just You have to know several rules... They are easily obtained...
My current (testing, mess but useful to learn how (or how not to) use it:```
:~$ cat .xinitrc#/usr/bin/xcompmgr &
/usr/bin/gnome-settings-daemon &
#/usr/bin/glipper &
#/usr/bin/indicator-weather &
/usr/bin/xset r rate 250 40 &
/usr/bin/setxkbmap -option lv3:ralt_switch,grp:sclk_toggle,grp_led:scroll,eurosign:5 rs,rs -variant latin, altwin:swap_lalt__lwin, caps:super &
/usr/bin/pulseaudio --daemonize &
#/usr/bin/pacmd set-source-volume alsa_output.usb-Burr-Brown_from_TI_USB_Audio_DAC-00-DAC.iec958-stereo.monitor 65536 &
#/usr/bin/awsetbg -f /home/zika/black_2048_1152.jpg &
#/usr/bin/awsetbg -f /home/zika/Pictures/BlackSnake.jpg &
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/awesome
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
#/usr/bin/ck-launch-session /usr/bin/gnome-session-fallback
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session-fallback
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-shell
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/dwm
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/fvwm
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/spectrwm
#/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/unity
#exec /usr/bin/ck-launch-session /usr/bin/gnome-session --session=gnome-fallback-compiz
#exec /usr/bin/ck-launch-session /usr/bin/gnome-session --session=gnome-fallback
#exec /usr/bin/ck-launch-session /usr/bin/awesome
exec /usr/bin/ck-launch-session /usr/bin/gnome-shell
#exec /usr/bin/ck-launch-session /usr/bin/unity
#exec /usr/bin/ck-launch-session /usr/bin/weston --fullscreen --backend=drm-backend.so
```

@zika,

Thanks very much. I think what to try is an experiment at terminal without using start x.  I want to create a script - ie;

(sleep 5; mir_demo_client_accelerated) & mir ; kill $!
(sleep 5; mir_demo_client_unaccelerated) & mir ; kill $!

and execute it at the tty prompt as I would, say for instance , MC (midnight-commander)

---

### Post by DisappearingOak on 2013-03-13
> **ventrical said:**
> Did you copy and paste or did you enter manually because there are spaces between certain arguments..

(sleep 5; mir_demo_accelerated)<space>&<space>mir<space>;<space>kill<space>$!

Either that or your hardware is too new.

Do you have all of these files?

Ahh. I was missing a couple files. Now mir does start. It gives me a colourful box with garbled lines at the top-left side of the screen.. and nothing. Then quitting it I see 'Segmentation fault error' core dumped. I tried the unaccelerated and only 'client' one also, and they give errors related to surface creation, etc.
(Radeon 4250 on AMD 880g)
I will post the entire error if it helps any devs once I google and know how to copy from the tty. But it might be known, I guess.

---

### Post by ventrical on 2013-03-13
> **DisappearingOak said:**
> Ahh. I was missing a couple files. Now mir does start. It gives me a colourful box with garbled lines at the top-left side of the screen.. and nothing. Then quitting it I see 'Segmentation fault error' core dumped. I tried the unaccelerated and only 'client' one also, and they give errors related to surface creation, etc.
(Radeon 4250 on AMD 880g)
I will post the entire error if it helps any devs once I google and know how to copy from the tty. But it might be known, I guess.


Don't forget to try a reboot (if you hadn't already) after loading those extra files.

---

### Post by ventrical on 2013-03-13
> **grahammechanical said:**
> some of us are also looking for instructions. This is about all that has been found so far. Well, it is all that I know. In the tty (Ctrl+Alt+F1 - in my case) try these three commands

```
(sleep 5; mir_demo_client) & mir; kill$!
```
```
(sleep 5; mir_demo_unaccelerated) & mir; kill$!
```
```
(sleep 5; mir_demo_accelerated) & mir; kill$!
```

What results do you get? To stop the demonstration press Ctrl+C. We get something with the accelerated demo but not much else with the other two demos. Ventrical worked out the 'sleep 5' = delay in running the demo. The lower the number the quicker the demo starts. The higher the number the longer the demo takes to start. So, wait a bit to see what happens before concluding that something is broken.

Sorry, I have nothing else to add. I have also installed the PPA for the Ubuntu Touch apps

@grahammechanical

 What is the ppa for this?

Thanks.
regards.

---

### Post by DisappearingOak on 2013-03-13
> **ventrical said:**
> Don't forget to try a reboot (if you hadn't already) after loading those extra files.

Yeah. It segfaults :)
-bash: line 2: 2390 Segmentation fault (core dumped) mir_demo_client_accelerated

that's all. I'll try mir again in some days when it is hopefully fixed.

---

### Post by grahammechanical on 2013-03-13
@ventrical

I thought that mention of The Touch core apps would get you interested.

[http://www.omgubuntu.co.uk/2013/03/how-to-play-with-ubuntu-touch-apps-in-ubuntu-12-10](http://www.omgubuntu.co.uk/2013/03/how-to-play-with-ubuntu-touch-apps-in-ubuntu-12-10)

Here is where I went from. It is only for 12.10 at the moment. After installing the PPA you need to install the apps but as of yesterday apps would not download due to missing libraries and Synaptic does not have them listed. so, I am assuming that those libraries are not yet in the repository.

[https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily](https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily)

To install one of the listed apps we try ```
sudo apt-get install ubuntu-calculator-app
``` for example. And follow that pattern for the rest. I have not succeeded so far. Oh, I see from that Launchpad link that apps are starting to appear for Raring. Things are moving along regarding MIR and these Touch core apps even if it does not seem very useful. We are at what Mark calls VERY BLEEDING EDGE. Only he does not need to shout. Not with us anyway.

Regards.

---

### Post by ventrical on 2013-03-13
> **grahammechanical said:**
> @ventrical

I thought that mention of The Touch core apps would get you interested.

[http://www.omgubuntu.co.uk/2013/03/how-to-play-with-ubuntu-touch-apps-in-ubuntu-12-10](http://www.omgubuntu.co.uk/2013/03/how-to-play-with-ubuntu-touch-apps-in-ubuntu-12-10)

Here is where I went from. It is only for 12.10 at the moment. After installing the PPA you need to install the apps but as of yesterday apps would not download due to missing libraries and Synaptic does not have them listed. so, I am assuming that those libraries are not yet in the repository.

[https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily](https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily)

To install one of the listed apps we try ```
sudo apt-get install ubuntu-calculator-app
``` for example. And follow that pattern for the rest. I have not succeeded so far. Oh, I see from that Launchpad link that apps are starting to appear for Raring. Things are moving along regarding MIR and these Touch core apps even if it does not seem very useful. We are at what Mark calls VERY BLEEDING EDGE. Only he does not need to shout. Not with us anyway.

Regards.

  I installed the ubuntu-calendar-app and it comes up nice in Unity but does nothing after you click it. No harm done I guess .. or do we have to enable ccsm  MTgrab handles to make it work?

 Also .. are the ubuntu-touch-apps related to MIR or should we start another thread for this?

edit: Ok .. the link says that the apps do actually 'nothing' at this stage :) lol

---

### Post by grahammechanical on 2013-03-13
At least the apps install now. I will try later tonight.

Edit: The PPA now works in Raring and the Touch Core Apps install. Which is progress. But they do not load. Pity. I would think that as these are the core apps of the Ubuntu touch devices and MIR is being developed as the display driver specifically for those Touch devices, then getting them running under MIR is the aim. I tried replacing a mir_demo name with a core app name but nothing happened except a blank screen. Still, we are on our way. Not going very fast, I admit. At least the development has been opened up to anyone who is a bit curious.

---

### Post by EgoGratis on 2013-03-13
It would be great if ubuntu-calendar-app would gain CalDAV support in not too distant future.

[http://www.youtube.com/watch?v=nSh14TWDHqY](http://www.youtube.com/watch?v=nSh14TWDHqY)

Then i would use it on desktop/mobile for sure. Something like this was available to Ubuntu users by default (clock/calendar indicator on the panel) until Evolution was dropped/replaced with Thunderbird but nice little app like this with CalDAV support i will say it again would be great for sure!

---

### Post by EgoGratis on 2013-03-13
This developer would be able to add CalDAV support for sure:

[https://syncevolution.org/](https://syncevolution.org/)

Because i do imagine this is quite big task. For e-mail (back-end) app [Yorba]("http://www.yorba.org/") could be approached?

---

### Post by EgoGratis on 2013-03-13
When all this things fall into place we will get Ubuntu DE i guess. At least on mobile.

Could some of the work from Sailfish OS be used? At least at the beginning to boost things up and then make in-house solutions if it makes sense but i think it would make more sense to start pushing devices and attracting 3rd party devs and to work on Mir in the beginning for example because it will take a lot of effort!

---

### Post by ventrical on 2013-03-14
> **grahammechanical said:**
> At least the apps install now. I will try later tonight.

Edit: The PPA now works in Raring and the Touch Core Apps install. Which is progress. But they do not load. Pity. I would think that as these are the core apps of the Ubuntu touch devices and MIR is being developed as the display driver specifically for those Touch devices, then getting them running under MIR is the aim. I tried replacing a mir_demo name with a core app name but nothing happened except a blank screen. Still, we are on our way. Not going very fast, I admit. At least the development has been opened up to anyone who is a bit curious.

  I think we are more or less getting framework files at this point, but, the mir server does work.  I think it is just the command line sturcture that we have to wait for (or keep experimenting with). Watch,wait and experiment. If I come up with anything I'll post it here first.

Still no word from Voss. His email box is probably crammed with bug reports.

EDIT:

18MB more of mir-doc files in updates.

---

### Post by ventrical on 2013-03-14
> **EgoGratis said:**
> When all this things fall into place we will get Ubuntu DE i guess. At least on mobile.

Could some of the work from Sailfish OS be used? 

I was presented with this 2 days ago but I am trying to focus on what I can do with MIR first and I had to give myself a refresh course in X and terminal commands.

I may even try it.

---

### Post by ventrical on 2013-03-14
The graphics we see when we use;

(sleep 5; mir_demo_client_accelerated)


is run by this script here:

```

/*
 * Copyright © 2012 Canonical Ltd.
 *
 * This program is free software: you can redistribute it and/or modify
 * it under the terms of the GNU General Public License version 3 as
 * published by the Free Software Foundation.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program.  If not, see <http://www.gnu.org/licenses/>.
 *
 * Authored by: Kevin DuBois   <kevin.dubois@canonical.com>
 */

#include "mir_toolkit/mir_client_library.h"
#include "mir/draw/graphics.h"

#include <assert.h>
#include <signal.h>
#include <string.h>
#include <stdio.h>
#include <unistd.h>
#include <getopt.h>
#include <EGL/egl.h>
#include <GLES2/gl2.h>

static char const *socket_file = "/tmp/mir_socket";
static MirConnection *connection = 0;
static MirSurface *surface = 0;

static void set_connection(MirConnection *new_connection, void * context)
{
    (void)context;
    connection = new_connection;
}

static void surface_create_callback(MirSurface *new_surface, void *context)
{
    (void)context;
    surface = new_surface;
}

static void surface_release_callback(MirSurface *old_surface, void *context)
{
    (void)old_surface;
    (void)context;
    surface = 0;
}

int main(int argc, char* argv[])
{
    int arg;
    opterr = 0;
    while ((arg = getopt (argc, argv, "hf:")) != -1)
    {
        switch (arg)
        {
        case 'f':
            socket_file = optarg;
            break;

        case '?':
        case 'h':
        default:
            puts(argv[0]);
            puts("Usage:");
            puts("    -f <socket filename>");
            puts("    -h: this help text");
            return -1;
        }
    }

    puts("Starting");

    mir_wait_for(mir_connect(socket_file, __PRETTY_FUNCTION__, set_connection, 0));
    puts("Connected");

    assert(connection != NULL);
    assert(mir_connection_is_valid(connection));
    assert(strcmp(mir_connection_get_error_message(connection), "") == 0);

    MirDisplayInfo display_info;
    mir_connection_get_display_info(connection, &display_info);
    assert(display_info.supported_pixel_format_items > 0);

    MirPixelFormat pixel_format = display_info.supported_pixel_format[0];

    MirSurfaceParameters const request_params =
        {__PRETTY_FUNCTION__, 640, 480, pixel_format, mir_buffer_usage_hardware};
    mir_wait_for(mir_surface_create(connection, &request_params, surface_create_callback, 0));
    puts("Surface created");

    assert(surface != NULL);
    assert(mir_surface_is_valid(surface));
    assert(strcmp(mir_surface_get_error_message(surface), "") == 0);

    /* egl setup */
    int major, minor, n, rc;
    EGLDisplay disp;
    EGLContext context;
    EGLSurface egl_surface;
    EGLConfig egl_config;
    EGLint attribs[] = {
        EGL_SURFACE_TYPE, EGL_WINDOW_BIT,
        EGL_RED_SIZE, 8,
        EGL_GREEN_SIZE, 8,
        EGL_BLUE_SIZE, 8,
        EGL_ALPHA_SIZE, 8,
        EGL_RENDERABLE_TYPE, EGL_OPENGL_ES2_BIT,
        EGL_NONE };
    EGLint context_attribs[] = { EGL_CONTEXT_CLIENT_VERSION, 2, EGL_NONE };

    EGLNativeDisplayType native_display = (EGLNativeDisplayType) mir_connection_get_egl_native_display(connection);
    EGLNativeWindowType native_window = (EGLNativeWindowType) mir_surface_get_egl_native_window(surface);
    assert(native_window != NULL);

    disp = eglGetDisplay(native_display);
    assert(disp != EGL_NO_DISPLAY);

    rc = eglInitialize(disp, &major, &minor);
    assert(rc == EGL_TRUE);
    assert(major == 1);
    assert(minor == 4);

    rc = eglChooseConfig(disp, attribs, &egl_config, 1, &n);
    assert(rc == EGL_TRUE);
    assert(n == 1);

    egl_surface = eglCreateWindowSurface(disp, egl_config, native_window, NULL);
    assert(egl_surface != EGL_NO_SURFACE);

    context = eglCreateContext(disp, egl_config, EGL_NO_CONTEXT, context_attribs);
    assert(egl_surface != EGL_NO_CONTEXT);

    rc = eglMakeCurrent(disp, egl_surface, egl_surface, context);
    assert(rc == EGL_TRUE);

    mir::draw::glAnimationBasic gl_animation;
    gl_animation.init_gl();

    for(;;)
    {
        gl_animation.render_gl();
        rc = eglSwapBuffers(disp, egl_surface);
        assert(rc == EGL_TRUE);

        usleep(167);//60fps

        gl_animation.step();
    }

    eglDestroySurface(disp, egl_surface);
    eglDestroyContext(disp, context);
    eglTerminate(disp);

    mir_wait_for(mir_surface_release(surface, surface_release_callback, 0));
    puts("Surface released");

    mir_connection_release(connection);
    puts("Connection released");

    return 0;
}



```

so we can adjust the variables to get different results.

More to come.

Edit:

If you want to examine all of the files for demo_examples then go to:

/usr/share/doc/libmirclient-demos/examples

You can open and examine them. They are written in C or C++. If you have any basic programming skill they are easily understood and rather simple subroutines.


 I am going to try to switch some variables a little later on and see what results I get. The moving image that we get comes from the data in the file mir_image.h and or graphics.h data.

---

### Post by ventrical on 2013-03-14
> **ventrical said:**
> The graphics we see when we use;

(sleep 5; mir_demo_client_accelerated)


is run by this script here:

```

/*
 * Copyright © 2012 Canonical Ltd.
 *
 * This program is free software: you can redistribute it and/or modify
 * it under the terms of the GNU General Public License version 3 as
 * published by the Free Software Foundation.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program.  If not, see <http://www.gnu.org/licenses/>.
 *
 * Authored by: Kevin DuBois   <kevin.dubois@canonical.com>
 */

#include "mir_toolkit/mir_client_library.h"
#include "mir/draw/graphics.h"

#include <assert.h>
#include <signal.h>
#include <string.h>
#include <stdio.h>
#include <unistd.h>
#include <getopt.h>
#include <EGL/egl.h>
#include <GLES2/gl2.h>

static char const *socket_file = "/tmp/mir_socket";
static MirConnection *connection = 0;
static MirSurface *surface = 0;

static void set_connection(MirConnection *new_connection, void * context)
{
    (void)context;
    connection = new_connection;
}

static void surface_create_callback(MirSurface *new_surface, void *context)
{
    (void)context;
    surface = new_surface;
}

static void surface_release_callback(MirSurface *old_surface, void *context)
{
    (void)old_surface;
    (void)context;
    surface = 0;
}

int main(int argc, char* argv[])
{
    int arg;
    opterr = 0;
    while ((arg = getopt (argc, argv, "hf:")) != -1)
    {
        switch (arg)
        {
        case 'f':
            socket_file = optarg;
            break;

        case '?':
        case 'h':
        default:
            puts(argv[0]);
            puts("Usage:");
            puts("    -f <socket filename>");
            puts("    -h: this help text");
            return -1;
        }
    }

    puts("Starting");

    mir_wait_for(mir_connect(socket_file, __PRETTY_FUNCTION__, set_connection, 0));
    puts("Connected");

    assert(connection != NULL);
    assert(mir_connection_is_valid(connection));
    assert(strcmp(mir_connection_get_error_message(connection), "") == 0);

    MirDisplayInfo display_info;
    mir_connection_get_display_info(connection, &display_info);
    assert(display_info.supported_pixel_format_items > 0);

    MirPixelFormat pixel_format = display_info.supported_pixel_format[0];

    MirSurfaceParameters const request_params =
        {__PRETTY_FUNCTION__, 640, 480, pixel_format, mir_buffer_usage_hardware};
    mir_wait_for(mir_surface_create(connection, &request_params, surface_create_callback, 0));
    puts("Surface created");

    assert(surface != NULL);
    assert(mir_surface_is_valid(surface));
    assert(strcmp(mir_surface_get_error_message(surface), "") == 0);

    /* egl setup */
    int major, minor, n, rc;
    EGLDisplay disp;
    EGLContext context;
    EGLSurface egl_surface;
    EGLConfig egl_config;
    EGLint attribs[] = {
        EGL_SURFACE_TYPE, EGL_WINDOW_BIT,
        EGL_RED_SIZE, 8,
        EGL_GREEN_SIZE, 8,
        EGL_BLUE_SIZE, 8,
        EGL_ALPHA_SIZE, 8,
        EGL_RENDERABLE_TYPE, EGL_OPENGL_ES2_BIT,
        EGL_NONE };
    EGLint context_attribs[] = { EGL_CONTEXT_CLIENT_VERSION, 2, EGL_NONE };

    EGLNativeDisplayType native_display = (EGLNativeDisplayType) mir_connection_get_egl_native_display(connection);
    EGLNativeWindowType native_window = (EGLNativeWindowType) mir_surface_get_egl_native_window(surface);
    assert(native_window != NULL);

    disp = eglGetDisplay(native_display);
    assert(disp != EGL_NO_DISPLAY);

    rc = eglInitialize(disp, &major, &minor);
    assert(rc == EGL_TRUE);
    assert(major == 1);
    assert(minor == 4);

    rc = eglChooseConfig(disp, attribs, &egl_config, 1, &n);
    assert(rc == EGL_TRUE);
    assert(n == 1);

    egl_surface = eglCreateWindowSurface(disp, egl_config, native_window, NULL);
    assert(egl_surface != EGL_NO_SURFACE);

    context = eglCreateContext(disp, egl_config, EGL_NO_CONTEXT, context_attribs);
    assert(egl_surface != EGL_NO_CONTEXT);

    rc = eglMakeCurrent(disp, egl_surface, egl_surface, context);
    assert(rc == EGL_TRUE);

    mir::draw::glAnimationBasic gl_animation;
    gl_animation.init_gl();

    for(;;)
    {
        gl_animation.render_gl();
        rc = eglSwapBuffers(disp, egl_surface);
        assert(rc == EGL_TRUE);

        usleep(167);//60fps

        gl_animation.step();
    }

    eglDestroySurface(disp, egl_surface);
    eglDestroyContext(disp, context);
    eglTerminate(disp);

    mir_wait_for(mir_surface_release(surface, surface_release_callback, 0));
    puts("Surface released");

    mir_connection_release(connection);
    puts("Connection released");

    return 0;
}



```

so we can adjust the variables to get different results.

More to come.

Edit:

If you want to examine all of the files for demo_examples then go to:

/usr/share/doc/libmirclient-demos/examples

You can open and examine them. They are written in C or C++. If you have any basic programming skill they are easily understood and rather simple subroutines.


 I am going to try to switch some variables a little later on and see what results I get. The moving image that we get comes from the data in the file mir_image.h and or graphics.h data.

Any ideas on a good compiler to make this executable? I have to replace mir_demo_client_accelerated executable with the new script compiled into executable format.

Thanks

---

### Post by dino99 on 2013-03-14
Try upp (u++)

---

### Post by ventrical on 2013-03-14
> **dino99 said:**
> Try upp (u++)

yes.. or g++

Thanks

---

### Post by ventrical on 2013-03-14
Run Midnight Commander in Mir

  I think I cracked the demo code. 

 If you want you can try this code to run Midnight Commander on the MIR server.
 First you have to have MC installed.

```

sudo apt-get install mc

```

After having all of you MIR files updated from the ppa run the code below on a terminal (CTRL+ALT+F1)

```


(sleep 200; mir) & mc ; kill $!


```

 The 200 represents 200 seconds that Midnight Commander will run *MC* on the mir server**. It will be fully functional but seems to  terminate after the alotted time frame.  To quit Midnight Commander just hit F10 then <yes> . Mir will exit normally. If it goes past timeframe it will terminate and you will need reboot CTRL+ALT+DEL.


 This test took place on a PC with these graphics card parameters:

```

 *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0

```
 and will try on Nvidia and ATi also.




Regards
Ventrical

---

### Post by ronacc on 2013-03-14
is there anyplace we can try ubuntu mobile , I have an acer iconia A100 I am willing to sacrifice to the cause .

---

### Post by zika on 2013-03-14
> **ventrical said:**
> Run Midnight Commander in Mir

  I think I cracked the demo code. 

 If you want you can try this code to run Midnight Commander on the MIR server.
 First you have to have MC installed.

```

sudo apt-get install mc

```

After having all of you MIR files updated from the ppa run the code below on a terminal (CTRL+ALT+F1)

```


(sleep 200; mir) & mc ; kill $!


```

 The 200 represents 200 seconds that Midnight Commander will run *MC* on the mir server**. It will be fully functional but seems to  terminate after the alotted time frame.  To quit Midnight Commander just hit F10 then <yes> . Mir will exit normally. If it goes past timeframe it will terminate and you will need reboot CTRL+ALT+DEL.


 This test took place on a PC with these graphics card parameters:

```

 *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0

```
 and will try on Nvidia and ATi also.




Regards
VentricalAren't You using ```
(sleep 200; mir) & mc ; kill $!
```a bit "backwards"...? If I read it properly You are not running MC in Mir at all...

---

### Post by zika on 2013-03-14
[http://www.phoronix.com/scan.php?page=news_item&px=MTMyNzM](http://www.phoronix.com/scan.php?page=news_item&px=MTMyNzM)

---

### Post by ventrical on 2013-03-14
> **zika said:**
> Aren't You using ```
(sleep 200; mir) & mc ; kill $!
```a bit "backwards"...? If I read it properly You are not running MC in Mir at all...


 Yes .. I am trying things backwards because there is basically not very much out there right now. I was able to prove the mir was actually running as a process using htop but, because of the way the code is set up  I am unable to sustain it and only get verification after I have exited. So you are correct. That was an erroneous assumption on my part.  All part of the fun of  working on teh edge of Ubuntu :) lol

---

### Post by ventrical on 2013-03-14
> **zika said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=MTMyNzM](http://www.phoronix.com/scan.php?page=news_item&px=MTMyNzM)

"There's also numerous Bazaar code branches appearing too that show early work on other functionality. "

Bazzaar??

EDIT .. Ok .. got it ;)

Still no new demo hacking codes.  So I'll keep hacking away at it here :)

---

### Post by zika on 2013-03-14
> **ventrical said:**
> Yes .. I am trying things backwards because there is basically not very much out there right now. I was able to prove the mir was actually running as a process using htop but, because of the way the code is set up  I am unable to sustain it and only get verification after I have exited. So you are correct. That was an erroneous assumption on my part.  All part of the fun of  working on teh edge of Ubuntu :) lolThis not on the edge, this is without reading man(ual)... ;)
> **ventrical said:**
> "There's also numerous Bazaar code branches appearing too that show early work on other functionality. "

Bazzaar??

EDIT .. Ok .. got it ;)

Still no new demo hacking codes. So I'll keep hacking away at it here :)It does not matter how You hold a hammer it will not become screwdriver or other tool by simply changing the way You handle it... We have to wait until development comes to some new point... But, if that makes You happy, who am I to try to discourage You...

---

### Post by ventrical on 2013-03-14
> **zika said:**
> This not on the edge, this is without reading man(ual)... ;)
It does not matter how You hold a hammer it will not become screwdriver or other tool by simply changing the way You handle it... We have to wait until development comes to some new point... But, if that makes You happy, who am I to try to discourage You...


Along as their is code to hack that's worth hacking .. I'm happy ! :) lol



.

---

### Post by ventrical on 2013-03-14
That's,

```


(sleep 30; mir) & mir & htop ; kill $!


```

It is very unstable. You have to CTRL+c  Then you have to hit enter so it will not lock up on you and blank the page  but you will see mir loaded in htop.

 Now to get it to run concurrent/stable.

---

### Post by zika on 2013-03-14
> **ventrical said:**
> That's,

```


(sleep 30; mir) & mir & htop ; kill $!


```

It is very unstable. You have to CTRL+c  Then you have to hit enter so it will not lock up on you and blank the page  but you will see mir loaded in htop.

 Now to get it to run concurrent/stable.Let us go step by step: What do You think this command does and what do You expect from it? 
```
(sleep 30; mir) & mir & htop ; kill $!
```
Would You try similar command with some other display server instead? What would You expect to happen?
Again, do You understand role of "&" in shell line?

---

### Post by ventrical on 2013-03-14
Thanks zika.

 I am now able to get htop to run stable.

The command is 

```


mir & htop


```

When htop loads it has  mir startx and then htop below it. It is a very simple code. It appears that mir is calling Xserver and then loading htop?

  It takes up 100% of one side of a dual core. I am not trying to be a pain.  Just  trying different code. I studied Vax Unix in 1990 and did batch files in the 80's with DOS. But Linux and  X  I am just getting a handle on.

So .. when I run 'mir" which is an executable file and use the "&" character to run 'htop' on mir (I assume). No man pages for mir as of yet. However mir is calling 'startx'. So .. if you decide to try it you will see 'mir startx' at the top of htop and htop below it.

 I'll get another pic.

---

### Post by ventrical on 2013-03-14
Pic of htop and mir.

---

### Post by zika on 2013-03-14
> **ventrical said:**
> Thanks zika.

 I am now able to get htop to run stable.

The command is 

```


mir & htop


```

When htop loads it has  mir startx and then htop below it. It is a very simple code. It appears that mir is calling Xserver and then loading htop?

  It takes up 100% of one side of a dual core. I am not trying to be a pain.  Just  trying different code. I studied Vax Unix in 1990 and did batch files in the 80's with DOS. But Linux and  X  I am just getting a handle on.

So .. when I run 'mir" which is an executable file and use the "&" character to run 'htop' on mir (I assume). No man pages for mir as of yet. However mir is calling 'startx'. So .. if you decide to try it you will see 'mir startx' at the top of htop and htop below it.

 I'll get another pic.No. Mir can not call Xserver since it should be sort of its replacement. A fact that they appear in htop list is just a fact that these processes are running... Order is not relevant to You... You're having two concurrent processes... You do not need man pages for mir, man for bash should be enough...
I thought that .xinitrc should be a sort of hint, with wayland/weston, etc...

---

### Post by ventrical on 2013-03-14
> **zika said:**
> No. Mir can not call Xserver since it should be sort of its replacement. A fact that they appear in htop list is just a fact that these processes are running... Order is not relevant to You... You're having two concurrent processes... You do not need man pages for mir, man for bash should be enough...
I thought that .xinitrc should be a sort of hint, with wayland/weston, etc...
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Yes it is a great hint.

  I am then curious as to why startx would not run before, only when I put in mir in the command line.

  I'll be doing some reading on this..
thanks again..

---

### Post by EgoGratis on 2013-03-14
I am not 100% sure but i do believe ATM you can't test much programs running natively on Mir. Just demos you tried. I am pretty sure everything else you are trying to test uses Xorg (on top of Mir).

---

### Post by ventrical on 2013-03-15
> **EgoGratis said:**
> I am not 100% sure but i do believe ATM you can't test much programs running natively on Mir. Just demos you tried. I am pretty sure everything else you are trying to test uses Xorg (on top of Mir).

This has been my assumption pretty well, however , I had not clearly stated it. So I can further declare my assumption that , yes , Mir is working in raring as per one of my screen shots documenting mir running in htop, in whatever limited capacity it is.

---

### Post by ventrical on 2013-03-15
> **ventrical said:**
> Thanks zika.

 I am now able to get htop to run stable.

The command is 

```


mir & htop


```

When htop loads it has  mir startx and then htop below it. It is a very simple code. It appears that mir is calling Xserver and then loading htop?

  It takes up 100% of one side of a dual core. I am not trying to be a pain.  Just  trying different code. I studied Vax Unix in 1990 and did batch files in the 80's with DOS. But Linux and  X  I am just getting a handle on.

So .. when I run 'mir" which is an executable file and use the "&" character to run 'htop' on mir (I assume). No man pages for mir as of yet. However mir is calling 'startx'. So .. if you decide to try it you will see 'mir startx' at the top of htop and htop below it.

 I'll get another pic.


 The above code will not work on Nividia G210/218 with nouveau.

---

### Post by cecilpierce on 2013-03-15
Tried the ppa, installed all the Mir stuff and alot of other junk, now I get a black screen and mouse pointer!
AND in a tty I get a big long blinking cursor, very interesting..:P

---

### Post by zika on 2013-03-15
> **ventrical said:**
> The above code will not work on Nividia G210/218 with nouveau.Should it?
Investigate proper usage of little we've got from PPA. It is just a beginning... It's just a feeble herald...

---

### Post by zika on 2013-03-15
> **cecilpierce said:**
> Tried the ppa, installed all the Mir stuff and alot of other junk, now I get a black screen and mouse pointer!
AND in a tty I get a big long blinking cursor, very interesting..:P
How do You "try" to "use&#711; it? Instead of what?

---

### Post by grahammechanical on 2013-03-15
@ventrical

I am running some of you experiments. And in my messing around a thought occurred to me. Midnight Commander and htop are text mode utilities. They will run in a tty anyway. How do we know that they are running on MIR? Regards.

---

### Post by ventrical on 2013-03-15
> **zika said:**
> Should it?
Investigate proper usage of little we've got from PPA. It is just a beginning... It's just a feeble herald...


 It works with the original hacking file code.

(sleep 5; mir_demo_client_accelerated) & mir ; kill $!

---

### Post by zika on 2013-03-15
> **ventrical said:**
> It works with the original hacking file code.

(sleep 5; mir_demo_client_accelerated) & mir ; kill $!Analyze that line. That is what I'm talking to You all the time. Yo've gone backwards, as I wrote...
Analyze why is demo_client postponed etc...
Analyze why I was using browser when I was testing weston not so long ago...
As Knuth said: "Picking test for randomness should not be done randomly"...
Here it should be: You can not use all possible permutations of this code-line to test sometjing... There should be some order... ;)

---

### Post by zika on 2013-03-15
This is nice...
You make me try Weston more and more often...
I'm writting this from FF-nightly in Weston while listening stream music... Pulseaudio works...
YouTube is OK, nice...
So, everything is in syntax... I've got it right now... FullScreen 2048x1152...
Waiting for Mir to catch up... ;)
Where is the catch in all I wrote above?
I was running it from X... So it does not count... ;) Same with Mir...
[http://wayland.freedesktop.org/xserver.html](http://wayland.freedesktop.org/xserver.html)

---

### Post by ventrical on 2013-03-15
> **grahammechanical said:**
> @ventrical

I am running some of you experiments. And in my messing around a thought occurred to me. Midnight Commander and htop are text mode utilities. They will run in a tty anyway. How do we know that they are running on MIR? Regards.


Good question . Answer... we don't know. At least I don't know. However, htop does show mir running (see my previous screenshot) and taking up 100% cpu.  The command;

```

mir &

```

means that mir should be running in the background. The ampersand  '&' after an executable 'mir' ensures that it does. However the ampersand '&' originally was used for GUI (Graphical User Interface), for example:

```

printconf-gui & <Enter>

```

"When running an X GUI utility at the command line the space and the "&" are not absolutely required. However if an X GUI utility is still running and you need to run another command at the command line (without opening another terminal emulation window, then you need to close the utility to be able to type in another command. Alternatively, you can open another terminal emulation window or go to a virtual terminal." Hello Linux, Lancom Technologies(C) 3-61 (from my old textbooks)

So .. when I use the code:

```

mir & htop

```

It is assumedly loading mir (which it does) as a graphical user interface and then htop is loaded also. But "mir" is not a GUI but an executable in /usr/bin/. Htop is a text program with ANSI graphics (I believe) and so it is an executable GUI so it does not need the <space> and the ampersand to execute.

 In one of my screen shots it shows the line <mir startx> apparently running concurrently, and , as pointed out, 'mir' is supposed to take the place of Xserver.

At this point I have not looked at the source code for 'mir' itself but I am assuming that there is a (startx) CALL in there some place or that mir calls a depend which calls startx.

  My best guesstimate at this time is that htop is running on x, side by side with mir but the logic would have it that htop is actually running on X which is using mir as a server. I can't prove this explicitly at this time and , as all have said .. it is still in the early stages, the bleeding edge as  the expression has been phrased.  I mean this is not about hammers and screw drivers. A screw driver can be used to pry somthing open. A hammer effectively can do the same thing in a quicker fashion and with a little more force. (bash it open) :) no pun intended! :) Using a hammer with a screwdriver becomes even more effective ! :)

Main thing .. I'm having a riot trying to break mir :) I thought that's why we are here? No?

Regards,
Ventrical

---

### Post by zika on 2013-03-15
Did You subscribe to Mir development mailing list?

---

### Post by ventrical on 2013-03-15
> **zika said:**
> Did You subscribe to Mir development mailing list?


I e-mailed Thomas Voss from launchpad asking for manuals. No word as of yet.

---

### Post by ventrical on 2013-03-15
> **zika said:**
> This is nice...
You make me try Weston more and more often...
I'm writting this from FF-nightly in Weston while listening stream music... Pulseaudio works...
YouTube is OK, nice...
So, everything is in syntax... I've got it right now... FullScreen 2048x1152...
Waiting for Mir to catch up... ;)
Where is the catch in all I wrote above?
I was running it from X... So it does not count... ;) Same with Mir...
[http://wayland.freedesktop.org/xserver.html](http://wayland.freedesktop.org/xserver.html)


I finally borked my mir code.

mir & htop

will no longer work, after update and reboot.

Real nice :)
have fun with Weston  n' Wayland and Willie Nelson too ! :)lol

---

### Post by ventrical on 2013-03-15
> **grahammechanical said:**
> @ventrical

I am running some of you experiments. And in my messing around a thought occurred to me. Midnight Commander and htop are text mode utilities. They will run in a tty anyway. How do we know that they are running on MIR? Regards.


@graham,

 Looks like I busted Mir (or the update/reboot busted it for me).

The code:

```


mir & htop


```

Will not longer work. 

Now it locks right up .. so I will have to go back to some more unorthodox code! :)

---

### Post by grahammechanical on 2013-03-15
@ventrical

this is what I was getting and remember this is Nvidia and Nouveau. So, bound to be messed up.

Run mir & htop in tty1 and htop blinked in and out of existence. Switched ttty7 and no desktop but nouveau messages and low resoultion mode mode dialog. Pressed Esc a couple of times to clear low resolution mode dialog. Switched back to tty1 and ran the command again and htop came up and stayed there. Yes, it shows MIR are taking up memory, several instances of MIR in fact but only small amounts of memory. And that is when I started thinking that htop may be running not on MIR but just in the tty.

Still it is fun experimenting.

---

### Post by ventrical on 2013-03-15
> **grahammechanical said:**
> @ventrical

this is what I was getting and remember this is Nvidia and Nouveau. So, bound to be messed up.

Run mir & htop in tty1 and htop blinked in and out of existence. Switched ttty7 and no desktop but nouveau messages and low resoultion mode mode dialog. Pressed Esc a couple of times to clear low resolution mode dialog. Switched back to tty1 and ran the command again and htop came up and stayed there. Yes, it shows MIR are taking up memory, several instances of MIR in fact but only small amounts of memory. And that is when I started thinking that htop may be running not on MIR but just in the tty.

Still it is fun experimenting.


 I agree. I got the exact same thing , did the exact same process you had detailed(on Nvidiamachine) only this time 'mir' is not running on top and using 100% CPU. Very . very interesting. it looks as if mir is just running as a static terminal, doing nothing.

---

### Post by serdotlinecho on 2013-03-16
[https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html](https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html)
[https://wiki.ubuntu.com/Mir/GetInvolved](https://wiki.ubuntu.com/Mir/GetInvolved)

---

### Post by zika on 2013-03-16
> **serdotlinecho said:**
> [https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html](https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html)
[https://wiki.ubuntu.com/Mir/GetInvolved](https://wiki.ubuntu.com/Mir/GetInvolved)
Now You're talking... Thank You.
Even more importants: upgrades are starting to trickle...
Update&#8321;: Operation on /etc/lightdm/lightdm.conf (type=mir) almost killed the patient LightDM... Easy resuscitation (removing that line) brought him back... Even though I do not use it (startx/xinit rules) it is nice to have him handy/alive...
Update&#8322;: Mesa packages from Mir-PPA did not kill anybody which is good news... Knock, knock, knock...

---

### Post by EgoGratis on 2013-03-16
Exciting indeed and i hope Unity Next (on Mir) will be available for testing soon. It looks like this project was well thought and now it's time to deliver! I am quite confident we will get something useful soon. The problem with Wayland is/was i knew it's going to happen but everybody talked about it in a way it wont happen in at least 5 years and that is to much and i hope Mir and Unity next and Wayland/Weston will be usable by end users in less then 2 years time.

---

### Post by ventrical on 2013-03-16
> **zika said:**
> Now You're talking... Thank You.
Even more importants: upgrades are starting to trickle...
Update&#8321;: Operation on /etc/lightdm/lightdm.conf (type=mir) almost killed the patient LightDM... Easy resuscitation (removing that line) brought him back... Even though I do not use it (startx/xinit rules) it is nice to have him handy/alive...
Update&#8322;: Mesa packages from Mir-PPA did not kill anybody which is good news... Knock, knock, knock...

Yep .. locked up two installs.. one on Nvidia and on on Intel graphics.

 At least I was able to load mir and show it running :) lol

---

### Post by ventrical on 2013-03-16
> **serdotlinecho said:**
> [https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html](https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html)
[https://wiki.ubuntu.com/Mir/GetInvolved](https://wiki.ubuntu.com/Mir/GetInvolved)


Thanks for sharing.

---

### Post by ventrical on 2013-03-16
Bwaaahahahahaha!! :) lol

  I just remembered .. I changed the name of 'mir' to sputnik .. so it should have been 'type=sputnik' :) lol

---

### Post by ventrical on 2013-03-16
> **EgoGratis said:**
> Exciting indeed and i hope Unity Next (on Mir) will be available for testing soon. It looks like this project was well thought and now it's time to deliver! I am quite confident we will get something useful soon. The problem with Wayland is/was i knew it's going to happen but everybody talked about it in a way it wont happen in at least 5 years and that is to much and i hope Mir and Unity next and Wayland/Weston will be usable by end users in less then 2 years time.


 I have been reading , reading  and from what I can tell from Mark's blogs and the rest of the team is that they are very enthusiastic about the whole project. And updates comming daily to mir-doc and the libs.

---

### Post by grahammechanical on 2013-03-16
A more appropriate name would have been Salyut = Fireworks. That's what goes off every time Ubuntu has something different. :) Just wait until we start getting Chinese words as code names! :)

---

### Post by ventrical on 2013-03-16
> **grahammechanical said:**
> A more appropriate name would have been Salyut = Fireworks. That's what goes off every time Ubuntu has something different. :) Just wait until we start getting Chinese words as code names! :)

 It will be Kung Fu fighting for Teenage Mutant Ninja Turtles! :) lol

---

### Post by ventrical on 2013-03-16
Here is a clip of the new mir demos so far:

[http://www.youtube.com/watch?v=gyGzxsILKz8&feature=youtu.be](http://www.youtube.com/watch?v=gyGzxsILKz8&feature=youtu.be)

This  on a Nvidia GeForce 210/218

```

oport:b0000000(size=536870912)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce G210]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0

```

so fooey to anyone who says I can't run it on Nvidia ! :) jk

---

### Post by ventrical on 2013-03-16
I guess the next question wil be ; Where do we get the Mesa, lightdm and xorg files  required to run mir?

"Note: for this to work you need to have Mir and all its dependencies  (which include lightdm, Mesa and the Xorg drivers). The easiest way is  to install pre-built packages from the staging PPA."

  I do have the ppa installed and working.

---

### Post by zika on 2013-03-16
> **ventrical said:**
> I guess the next question wil be ; Where do we get the Mesa, lightdm and xorg files  required to run mir?

"Note: for this to work you need to have Mir and all its dependencies  (which include lightdm, Mesa and the Xorg drivers). The easiest way is  to install pre-built packages from the staging PPA."

  I do have the ppa installed and working.
From MirPPA, arrived this morning and pulled just OK...
Nice play with Mir:
[http://www.youtube.com/watch?v=5mS9dyVTTl8](http://www.youtube.com/watch?v=5mS9dyVTTl8)
;)

---

### Post by ventrical on 2013-03-16
> **zika said:**
> From MirPPA, arrived this morning and pulled just OK...
Nice play with Mir:
[http://www.youtube.com/watch?v=5mS9dyVTTl8](http://www.youtube.com/watch?v=5mS9dyVTTl8)
;)


 So many hours on the keyboard. I need comic relief once in while.  Talking to stuffed animals helps me think outside the box. :)

---

### Post by cariboo on 2013-03-16
> **ventrical said:**
> So many hours on the keyboard. I need comic relief once in while.  Talking to stuff animals helps me think outside the box. :)

If that's what floats your boat, go for it. :-D

---

### Post by grahammechanical on 2013-03-16
What I think is scary is the fact that you understand every word the beaver is saying. :) :)

---

### Post by ventrical on 2013-03-16
> **grahammechanical said:**
> What I think is scary is the fact that you understand every word the beaver is saying. :) :)


haheahehahaha... That was 4 years ago I did that . A message to my cousin up north .. but I just uploaded it recently. I was just horseing around. I thought I had locked it out .. Whoops! :)

---

### Post by ventrical on 2013-03-16
> **cariboo907 said:**
> If that's what floats your boat, go for it. :-D


Apologies for being off topic. :)

---

### Post by DisappearingOak on 2013-03-17
A quick question - I have Ubuntu installed in a separate partition just for testing and have other installations so I'm not worried about borking the software by trying mir. But I was concerned.. I want to test mir but I want to know.. it won't affect the hardware, will it?

---

### Post by dino99 on 2013-03-17
right now its no more than a stupid video demo  :(

---

### Post by grahammechanical on 2013-03-17
> **DisappearingOak said:**
> A quick question - I have Ubuntu installed in a separate partition just for testing and have other installations so I'm not worried about borking the software by trying mir. But I was concerned.. I want to test mir but I want to know.. it won't affect the hardware, will it?

I do not think so. At present Mir is a long way from being a display service. I think development work will happen fast but at the moment it is sitting on the Xserver. Once it becomes a stand-alone display server then I guess it will have to be able to set the correct resolutions for monitors. There are some things to watch out for.

[http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html](http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html)

[http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)

I edited the lightdm.conf file as instructed and now I get a tty1 prompt. I mess around a bit and get a desktop with out Unity. I guess I missed something out. That is not unusual for me. You might also want to install the Ubuntu Touch core apps. There is now a daily PPA for Raring. Click Technical details about this PPA and Choose your Ubuntu.

[https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily](https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily)

[http://www.omgubuntu.co.uk/2013/03/how-to-play-with-ubuntu-touch-apps-in-ubuntu-12-10](http://www.omgubuntu.co.uk/2013/03/how-to-play-with-ubuntu-touch-apps-in-ubuntu-12-10)

These are the mobile core apps and they are supposed to run on Mir. They do not do anything at the moment. They are just icons in the Dash. But it is a way of watching things get developed.

Regard

---

### Post by serdotlinecho on 2013-03-18
> **dino99 said:**
> right now its no more than a stupid video demo  :(


[Another]("http://www.youtube.com/watch?v=pSs9airQmcQ") stupid video for us to enjoy. :lolflag:
[COLOR=#333333][FONT=arial]^^^
*XMir: Metacity and cairogears running on top of X running against Mir (free driver stack)* [/FONT][/COLOR]

---

### Post by ventrical on 2013-03-18
> **grahammechanical said:**
> I do not think so. At present Mir is a long way from being a display service. I think development work will happen fast but at the moment it is sitting on the Xserver. Once it becomes a stand-alone display server then I guess it will have to be able to set the correct resolutions for monitors. There are some things to watch out for.

[http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html](http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html)

[http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)

I edited the lightdm.conf file as instructed and now I get a tty1 prompt. I mess around a bit and get a desktop with out Unity. I guess I missed something out. That is not unusual for me. You might also want to install the Ubuntu Touch core apps. There is now a daily PPA for Raring. Click Technical details about this PPA and Choose your Ubuntu.

[https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily](https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily)

[http://www.omgubuntu.co.uk/2013/03/how-to-play-with-ubuntu-touch-apps-in-ubuntu-12-10](http://www.omgubuntu.co.uk/2013/03/how-to-play-with-ubuntu-touch-apps-in-ubuntu-12-10)

These are the mobile core apps and they are supposed to run on Mir. They do not do anything at the moment. They are just icons in the Dash. But it is a way of watching things get developed.

Regard

 There is a  mir.log  file @ /var/log/lightdm/mir.log

 Mine had reported:

'ERROR: /build/buildd/mir-0.0.2bzr504raring0/src/server/graphics/gbm/gbm_display_buffer.cpp(137): Throw in function mir::graphics::gbm::GBMDisplayBuffer::GBMDisplayBuffer(const std::shared_ptr<mir::graphics::gbm::GBMPlatform>&, const std::shared_ptr<mir::graphics::DisplayReport>&, const std::vector<std::shared_ptr<mir::graphics::gbm::KMSOutput> >&, mir::graphics::gbm::GBMSurfaceUPtr, const mir::geometry::Size&, EGLContext)
Dynamic exception type: boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<std::runtime_error> >
std::exception::what: Failed to get frontbuffer
'

---

### Post by ventrical on 2013-03-18
Entering the code:

```

ps aux | grep mir
[/CODE

should give results in the following:

1000    ####  0.0  0.0   ####  812 tty1   S +15:00  0:00  grep --color=auto mir 

mir should be highlighted in red.

Then:

[CODE]
sudo mir stop

```

My screen went blank, then black and naturaly lost my desktop at tty7, but I was still able to get back to tty1.

 I had to log back on .. so what I think mir did was actually log me out when I entered the above code.

 I didn't get any errors, so I ** assume** mir must be running in the background.

 restarting lighdm does not reload the desktop so far on two of my machines.

regards,
ventrical

---

### Post by zika on 2013-03-18
> **ventrical said:**
> Entering the code:

```

ps aux | grep mir

```

should give results in the following:

1000    ####  0.0  0.0   ####  812 tty1   S +15:00  0:00  grep --color=auto mir 

mir should be highlighted in red.
That line shows that You were grep-ing (pipeing in grep) for mir the output of „ps aux“ not that any instance of mir is present and running...
As I've already said You have to learn to interpret results...

To show, this is the output at my machine without anything near mir for several days... ;)
```
:~$ ps aux|grep mir
********      5854  0.0  0.0   9440   924 pts/0    S+   21:37   0:00 grep --color=auto mir
```



> **ventrical said:**
> Then:

```

sudo mir stop

```

My screen went blank, then black and naturaly lost my desktop at tty7, but I was still able to get back to tty1.

 I had to log back on .. so what I think mir did was actually log me out when I entered the above code.

 I didn't get any errors, so mir must be running in the background.

 restarting lighdm does not reload the desktop so far on two of my machines.

regards,
ventricalWhat instance of mir was stopped if it was not running at all?

---

### Post by EgoGratis on 2013-03-18
[http://www.iloveubuntu.net/mir-received-updated-full-informations-webpage-strengthens-its-collaborative-community-open-attitude](http://www.iloveubuntu.net/mir-received-updated-full-informations-webpage-strengthens-its-collaborative-community-open-attitude)

---

### Post by ventrical on 2013-03-18
> **zika said:**
> That line shows that You were grep-ing (pipeing in grep) for mir the output of &#8222;ps aux&#8220; not that any instance of mir is present and running...
As I've already said You have to learn to interpret results...

To show, this is the output at my machine without anything near mir for several days... ;)
```
:~$ ps aux|grep mir
********      5854  0.0  0.0   9440   924 pts/0    S+   21:37   0:00 grep --color=auto mir
```



What instance of mir was stopped if it was not running at all?

[SIZE=1]

[/SIZE]

  I have no idea.  I am just following the instructions to the links. They said to add mir=type to the lightdm.conf file THEN sudo service lightdm restrart (and I did) and I lost desktop but still had terminal so I just tried  and experiment. There is not much to run on here .. so I'm just  trying different things and posting them up here as I test them. 'Anyone got MIR working in raring?' is the topic?

[SIZE=1]

[/SIZE]

---

### Post by ventrical on 2013-03-18
> **zika said:**
> That line shows that You were grep-ing (pipeing in grep) for mir the output of „ps aux“ not that any instance of mir is present and running...
As I've already said You have to learn to interpret results...

To show, this is the output at my machine without anything near mir for several days... ;)
```
:~$ ps aux|grep mir
********      5854  0.0  0.0   9440   924 pts/0    S+   21:37   0:00 grep --color=auto mir
```



What instance of mir was stopped if it was not running at all?

 
 I just did another experiment in terminal using an non existant name between sudo and stop in tty1.

```

sudo  _name_  stop

```

 and I got:

'command not found'

 So .. you tell me why  my screen dumped to black when I entered;

```


sudo mir stop


```

 So .. if mir is not loaded .... then why would this X terminal  command not produce the same results.??

---

### Post by ventrical on 2013-03-18
> **EgoGratis said:**
> [http://www.iloveubuntu.net/mir-received-updated-full-informations-webpage-strengthens-its-collaborative-community-open-attitude](http://www.iloveubuntu.net/mir-received-updated-full-informations-webpage-strengthens-its-collaborative-community-open-attitude)


Great info.  I have wore out that code from the hacking.file .. and I had to move on to try other methods of trying to hack and disassemble mir.

---

### Post by zika on 2013-03-19
> **ventrical said:**
> I have no idea.  I am just following the instructions to the links. They said to add mir=type to the lightdm.conf file THEN sudo service lightdm restrart (and I did) and I lost desktop but still had terminal so I just tried  and experiment.** There is not much to run on here .. so I'm just  trying different things and posting them up here as I test them. 'Anyone got MIR working in raring?' is the topic?**
> **ventrical said:**
> Great info.  I have wore out that code from the hacking.file .. and I had to move on to try other methods of trying to **hack and disassemble** mir.Every finite set has only finite number of permutations of its members... Some of them might make sense, some of them not... Like taking several letters and shuffling them. Sometimes You get a proper word, lot of time You get just...
Have fun. You should get source of Mir and start from there... ;)

---

### Post by ventrical on 2013-03-19
> **zika said:**
> You should get source of Mir and start from there... ;)

Thats what I have been doing on the side.

---

### Post by ventrical on 2013-03-19
Mir Breakage:

  With the lightdm.conf restored to normal  (no type=mir) I  rebooted  and got this.

Edit: Hard rebooted and problem gone.

---

### Post by ventrical on 2013-03-19
> **zika said:**
> Every finite set has only finite number of permutations of its members... Some of them might make sense, some of them not...

I am not totally disputing this .  I just like to experiment with those different sets and functions. What may be standard for one machine might not be the case for another. So we all have different results, or, at times we can emulate the exact results. So there is lots to learn :)

Thanks,

Regards,

ventrical

---

### Post by zika on 2013-03-19
> **ventrical said:**
> Thats what I have been doing on the side.Nice... Expecting faster development of Mir already...

---

### Post by grahammechanical on 2013-03-19
@ventrical

> [COLOR=#000000]restarting lighdm does not reload the desktop so far on two of my machines.[/COLOR]

And there was I thinking that I must be doing something wrong. And then there is this

> [COLOR=#000000][FONT=Roboto]Make sure your hardware is supported. That means you're using a Mesa driver, of which only intel and radeon families are presently supported.[/FONT][/COLOR] And yet both you and I can run at least one of the demonstrations on Nvidia adapters. Still at least we are at the "bleeding edge" even if it is not yet "awesome." :)

---

### Post by serdotlinecho on 2013-03-19
[OFFTOPIC]The X.Org Foundation Is [Undecided]("http://www.phoronix.com/scan.php?page=news_item&px=MTMzMDM") About Mir[/OFFTOPIC]

---

### Post by grahammechanical on 2013-03-19
> **serdotlinecho said:**
> [OFFTOPIC]The X.Org Foundation Is [Undecided]("http://www.phoronix.com/scan.php?page=news_item&px=MTMzMDM") About Mir[/OFFTOPIC]

Perhaps they should read the Mir specification

> [COLOR=#333333][FONT=Ubuntu Beta]For the desktop/laptop form-factor, we want to fully replace X _in user sessions_ and provide a legacy mode that allows to run legacy X clients against _an on-demand rootless X server_[/FONT][/COLOR]


In my ignorance I do not see this roadmap as a claim to replace X on the desktop in 12 months.

---

### Post by ventrical on 2013-03-19
> **grahammechanical said:**
> @ventrical



And there was I thinking that I must be doing something wrong. And then there is this

 And yet both you and I can run at least one of the demonstrations on Nvidia adapters. Still at least we are at the "bleeding edge" even if it is not yet "awesome." :)

  The documentation so far is not updated regularily and is missing a few steps. ie;

Here is an excerpt from "Using Mir on a PC"

> 
To run X sessions under Mir, with Mir acting as the system  compositor, edit your /etc/lightdm/lightdm.conf to look to look like  this: 
 
[SeatDefaults] user-session=ubuntu greeter-session=unity-greeter type=mir Now restart lightdm: 
 
$ sudo service lightdm restart In theory, you should now find yourself back in Ubuntu and not  notice anything different. You can verify you're in mir several ways:


  It tells us to restart lighdm but it does not say from where. From tty1?  From gnome-terminal?  Do we change lighdm.cong with gksu gedit?  So there are some holes here of course. In theory we *should* find ourselves back in Ubuntu but in practice we do not.

As for being at the bleeding edge .. yes ... I like working on these newer modules.  It will be interesting to see if it actually does become 'awesome'.! :)

---

### Post by ventrical on 2013-03-19
> **zika said:**
> Nice... Expecting faster development of Mir already...


With your help it will be a masterpiece...

---

### Post by zika on 2013-03-19
> **ventrical said:**
> With your help it will be a masterpiece...No, I do not have enough knowledge to embark in such endeavour... I'm just a simple tester...> **ventrical said:**
> The documentation so far is not updated regularily and is missing a few steps. ie;
Here is an excerpt from "Using Mir on a PC"
It tells us to restart lighdm but it does not say from where. From tty1? From gnome-terminal? Do we change lighdm.cong with gksu gedit? So there are some holes here of course. **In theory we *should* find ourselves back in Ubuntu but in practice we do not.**
As for being at the bleeding edge .. yes ... I like working on these newer modules. It will be interesting to see if it actually does become 'awesome'.! :)You can use (I suppose) any editor You use for programmng, let alone any text-editor either in GUI or CLI... I'm sure You have favourite one... Restart of DM is (as far as I know) prefered to be done outside the DM... I did not understand where did You find Yourself (see bold-ed)...
To my taste documentation is adequate for current state of Mir...

---

### Post by dino99 on 2013-03-19
I cant wait any more, give me your zika.xml & ventrical.xml :P with plenty of nice mir features  and bugs fixed :lolflag:

---

### Post by zika on 2013-03-19
> **dino99 said:**
> I cant wait any more, give me your zika.xml & ventrical.xml :P with plenty of nice mir features  and bugs fixed :lolflag:[http://www.youtube.com/watch?v=Reqc38YW81w](http://www.youtube.com/watch?v=Reqc38YW81w)

... [img]http://ubuntuforums.org/images/smilies/smiley-faces-75.gif[/img]

---

### Post by ventrical on 2013-03-19
> **zika said:**
> No, I do not have enough knowledge to embark in such endeavour... I'm just a simple tester...You can use (I suppose) any editor You use for programmng, let alone any text-editor either in GUI or CLI... I'm sure You have favourite one... Restart of DM is (as far as I know) prefered to be done outside the DM... I did not understand where did You find Yourself (see bold-ed)...
To my taste documentation is adequate for current state of Mir...


 I thought that meant  the 'Ubuntu Desktop DE', not just the Xterminal .. or at least lightdm.

---

### Post by zika on 2013-03-19
> **ventrical said:**
> I thought **that** meant  the 'Ubuntu Desktop DE', not just the Xterminal .. or at least lightdm.I did not understand this... What did You mean by "that"...?

---

### Post by ventrical on 2013-03-19
> **zika said:**
> I did not understand this... What did You mean by "that"...?

                     [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **ventrical**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12564671#post12564671")                 

                 The documentation so far is not updated regularily and is missing a few steps. ie;
Here is an excerpt from "Using Mir on a PC"
It tells us to restart lighdm but it does not say from where. From tty1?  From gnome-terminal? Do we change lighdm.cong with gksu gedit? So there  are some holes here of course. **In theory we *should* find ourselves back in Ubuntu but in practice we do not.**
As for being at the bleeding edge .. yes ... I like working on these  newer modules. It will be interesting to see if it actually does become  'awesome'.! :smile:

As the original mir-doc stated, I assumed after editing the lighdm.conf file, then, sudo restart lightdm *or* sudo service lightdm restart that  I would end up back in the Ubuntu Desktop. The mir-doc said "Ubuntu" but what part of Ubuntu are they talking about.?

'that' meaning that the writers of How to run Mir of PC meant  Ubuntu Desktop.

---

### Post by ventrical on 2013-03-19
> **zika said:**
> I did not understand this... What did You mean by "that"...?

Please look at the bottom line of this screenshot.

---

### Post by ventrical on 2013-03-19
'Mir C++ Style Guide'

can be downloaded from launchpad.

cppguide.xml
styleguide.css
styleguide.xsl

[http://bazaar.launchpad.net/~mir-team/mir/trunk/files/head:/guides/](http://bazaar.launchpad.net/~mir-team/mir/trunk/files/head:/guides/)

---

### Post by zika on 2013-03-20
> **ventrical said:**
> Please look at the bottom line of this screenshot.
Can You click on PageDown... ;)
Wasn't it easier to just give [URL](http://unity.ubuntu.com/mir/using_mir_on_pc.html)... ;)
Have fun... ;)

---

### Post by zika on 2013-03-20
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzMjI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzMjI)
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzMTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTMzMTQ)

---

### Post by ventrical on 2013-03-20
> **zika said:**
> Can You click on PageDown... ;)
Wasn't it easier to just give [URL]("http://unity.ubuntu.com/mir/using_mir_on_pc.html")... ;)
Have fun... ;)


[http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)

---

### Post by grahammechanical on 2013-03-20
I can tell you this, editing lightdm.conf according to instructions and restarting lightdm by a reboot gets me to a black screen.  A completely dead black screen not a tty. I now have to find a way of removing "type=mir" from lightdm.conf without being at a desktop. There are two other ways of running the command "sudo service lightdm restart" that I can think of. From a terminal on the desktop and from a tty. Both fail to get me back to a working Ubuntu. 

And I also understand this in the Mir guide to mean a normal Ubuntu desktop with all applications. > [COLOR=#000000]*In theory, you should now find yourself back in Ubuntu and not notice anything different.*[/COLOR] This little experiment is turning into a good practice session for developing skills in fixing broken desktops.

---

### Post by dino99 on 2013-03-20
booting in recovery mode might let you edit lightdm.conf (with nano), or chroot via ssh

---

### Post by ventrical on 2013-03-20
> **grahammechanical said:**
> I can tell you this, editing lightdm.conf according to instructions and restarting lightdm by a reboot gets me to a black screen.  A completely dead black screen not a tty. I now have to find a way of removing "type=mir" from lightdm.conf without being at a desktop. There are two other ways of running the command "sudo service lightdm restart" that I can think of. From a terminal on the desktop and from a tty. Both fail to get me back to a working Ubuntu. 

And I also understand this in the Mir guide to mean a normal Ubuntu desktop with all applications.  This little experiment is turning into a good practice session for developing skills in fixing broken desktops.

 That  is precisely what I am getting and I have the Intel and  ATi  graphics card capabilities, however it does not mention (that I can find) what graphics card they are using exactly. That leads me to assume that the particular document in question was not meant for us here at U+1. Either that or the instructions are erroneous , because they are obviously incomplete at best.  However , the Demos work exceptionally well. I can at least do some manouvering and manipulating of those demo lines of code that are suggested  to vary the results.

  I have also learned that when my desktop was broken by my experiments that I could always reboot (CTRL+ALT+DEL) from the *RIGHT* hand side of the keyboard. The ALT +F1 or ALT+F2 as suggested in the manual does nothing here across various 'from factors'. :) 

  I am also able to get mir to come up in htop  from gnome-terminal on Ubuntu Desktop (without the <type=mir> in the lightdm.conf file) when I drop down to kernel 3.9.0-9, 3.8.0-10 but not higher, so I assume there is a kernel patch problem also.

Regardless the problems I am still having a great time experimenting. Big update today ... let's see.... :)

---

### Post by ventrical on 2013-03-20
> **grahammechanical said:**
> I can tell you this, editing lightdm.conf according to instructions and restarting lightdm by a reboot gets me to a black screen.  A completely dead black screen not a tty. I now have to find a way of removing "type=mir" from lightdm.conf without being at a desktop. .


 I have stable installs on most of my machines so I boot there from Grub, open Gnome terminal, click on nautilus and make sure I have the drive mounted <click> then :

gksu gedit /etc/lightdm/ lightdm.conf

 Or I Believe you can do the same from a USB iso "live".

---

### Post by ventrical on 2013-03-20
> **dino99 said:**
> booting in recovery mode might let you edit lightdm.conf (with nano), or chroot via ssh


Yes.. nice indeed. :) I forgot about nano. Doh!

Thanks.

Edit:

  I am able to  edit in and edit out and get back to a working Ubuntu-Desktop.

---

### Post by grahammechanical on 2013-03-20
Thanks for the tip about nano. I knew I would get advice about a command line editor. A thougth has also occurred to me. Surely the correct procedure is to first stop lightdm and then restart lightdm? And not just restart it. If we wanted to switch to GDM, we would first stop LighDM and then start gdm. Is that not the correct procedure?

---

### Post by zika on 2013-03-20
> **ventrical said:**
> [http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)You did not click on „URL“ marked field in my message that You've quoted...? ;)

---

### Post by zika on 2013-03-20
> **grahammechanical said:**
> I can tell you this, editing lightdm.conf according to instructions and restarting lightdm by a reboot gets me to a black screen.  A completely dead black screen not a tty. I now have to find a way of removing "type=mir" from lightdm.conf without being at a desktop. There are two other ways of running the command "sudo service lightdm restart" that I can think of. From a terminal on the desktop and from a tty. Both fail to get me back to a working Ubuntu. 

And I also understand this in the Mir guide to mean a normal Ubuntu desktop with all applications.  This little experiment is turning into a good practice session for developing skills in fixing broken desktops.
TTY 101:
No need for reboot and recovery mode, in most cases, with Mir not neccessary...
Ctrl-Alt-Fn, n in {1,2,3,4,5,6} would get You to ttyn... tty7 and tty8 are for GUI... Ctr-Alt-Fm, m in {6,7} work for them...
In there, after login You could use```
sudo nano /etc/lightdm/lightdm.conf
```
To stop LightDM```
sudo service lightdm stop
```
To start LightDM```
sudo service lightdm start
```
To restart LightDM```
sudo service lightdm restart
```
Have fun...

---

### Post by ventrical on 2013-03-20
> **zika said:**
> You did not click on „URL“ marked field in my message that You've quoted...? ;)


Didn't see it. ;)

---

### Post by ventrical on 2013-03-20
> **grahammechanical said:**
> Thanks for the tip about nano. I knew I would get advice about a command line editor. A thougth has also occurred to me. Surely the correct procedure is to first stop lightdm and then restart lightdm? And not just restart it. If we wanted to switch to GDM, we would first stop LighDM and then start gdm. Is that not the correct procedure?

 Sorry to be off topic.

 I just realized that there may be a problem with my testing. I have a quad set of towers running off a KVM. This may be causing a syncing issue or a modeset issue.

On Topic:

 I noticed some  changes in /Xorg.0.log and  I was wondering  how to change  modeset in New Grub configuration of raring  to "nomodeset".

 I just want to try another experiment.

---

### Post by zika on 2013-03-20
> **ventrical said:**
> Sorry to be off topic.

 I just realized that there may be a problem with my testing. I have a quad set of towers running off a KVM. This may be causing a syncing issue or a modeset issue.

On Topic:

 I noticed some  changes in /Xorg.0.log and  I was wondering  how to change  modeset in New Grub configuration of raring  to "nomodeset".

 I just want to try another experiment.
With which kernel and driver. "Nomodesset" was depreciated not so long ago... If You're u-to-date there might be no way of going nomodeset any more...
If You still need help how to change Grub, shout...

---

### Post by grahammechanical on 2013-03-20
Nomodeset depreciated? Richard Stallman never said anything to me. That is it. I going over to Lilo!

@ventrical

At the grub menu select Ubuntu and press E. That puts grub in Edit mode. Look for the line that says

> initrd.lz quiet splash and change it to > initrd.lz nomodest quiet splash You can Esc out and then boot. This will only work that once it does not permanently edit the Grub boot parameters.

Regards.

---

### Post by zika on 2013-03-20
> **grahammechanical said:**
> Nomodeset depreciated? Richard Stallman never said anything to me. That is it. I going over to Lilo!

@ventrical

At the grub menu select Ubuntu and press E. That puts grub in Edit mode. Look for the line that says

 and change it to  You can Esc out and then boot. This will only work that once it does not permanently edit the Grub boot parameters.

Regards.
I might be wrong, RS might forgot to inform You...
```
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-13-generic root=UUID=402a564e-c124-4fac-9be5-28afc310e2d5 ro nomodeset apparmor=0
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-13-generic root=UUID=402a564e-c124-4fac-9be5-28afc310e2d5 ro nomodeset apparmor=0
[   10.465401] [drm] radeon kernel modesetting enabled.
[   10.465716] [drm] initializing kernel modesetting (RV635 0x1002:0x9598 0x1043:0x01DA).

```
With radeon.modeset=0 its completely another story...
Be prepared for lower resolution...
```
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-13-generic root=UUID=402a564e-c124-4fac-9be5-28afc310e2d5 ro radeon.modeset=0 apparmor=0
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-13-generic root=UUID=402a564e-c124-4fac-9be5-28afc310e2d5 ro radeon.modeset=0 apparmor=0
```

---

### Post by ventrical on 2013-03-20
> **grahammechanical said:**
> Nomodeset depreciated? Richard Stallman never said anything to me. That is it. I going over to Lilo!

@ventrical

At the grub menu select Ubuntu and press E. That puts grub in Edit mode. Look for the line that says

 and change it to  You can Esc out and then boot. This will only work that once it does not permanently edit the Grub boot parameters.

Regards.

Zika is right. I tried that, got  Ubuntu Desktop, really slow and sluggish, then, went to terminal and got vertical blue stripes (Ubuntu Blue screen of Death?)  All is well again. However, I learned something new. I was wondering why  when I chose nomodeset from Raring USB install that all of those installs ran like they had molases stuck to them. So, when ticing off <nomodeset> during  install carries over to the Ubuntu-Desktop .. or even Grub?

<not intentionally trying to be off topic here> I just thought that the above might be a note of interest  already noted.

Thanks for your help Graham.

---

### Post by ventrical on 2013-03-20
> **ventrical said:**
> Sorry to be off topic.

 I just realized that there may be a problem with my testing. I have a quad set of towers running off a KVM. This may be causing a syncing issue or a modeset issue.

On Topic:

 I noticed some  changes in /Xorg.0.log and  I was wondering  how to change  modeset in New Grub configuration of raring  to "nomodeset".

 I just want to try another experiment.

 Tried everything. Removed PC from KVM, purged and re-installed mir/ppa.

type=mir still gives me just gives me black-screen. Perhaps those tests are run in a cadence controlled environment.

---

### Post by ventrical on 2013-03-20
I switched over to a higher end ATi graphics card. I almost had it working :) but there was a driver version error. The thing is , I had all of this nice info in /var/log/lightdm/mir.log and then when I went to copy and paste it I entered the wrong gksu code and the data is now gone !! So I would have to do the procedure all over again :) .

Break time ! ;)

---

### Post by grahammechanical on 2013-03-21
@ventrical

I found out how to get those Touch core apps working. The answer - install the SDK preview. It must bring in some libraries that do not come in through the PPA.

[http://developer.ubuntu.com/get-started/gomobile/](http://developer.ubuntu.com/get-started/gomobile/)

I installed the SDK thinking that I might be able to run the apps through it but after the download had finished it was possible to launch any of the apps that were installed directly from the Dash without QTCreator loaded. I am still not having any success with the "type=mir" problem. Even "lightdm stop" followed by "lighdm start" does not make any difference. Still, at least I can use Nano to remove "type=mir" from the lightdm configuration file. I have been wondering why there is the instruction to restart lightdm. Finally worked out the reason. It is simply like logging out and logging back in.

---

### Post by ventrical on 2013-03-21
> **grahammechanical said:**
> @ventrical

I found out how to get those Touch core apps working. The answer - install the SDK preview. It must bring in some libraries that do not come in through the PPA.

[http://developer.ubuntu.com/get-started/gomobile/](http://developer.ubuntu.com/get-started/gomobile/)

I installed the SDK thinking that I might be able to run the apps through it but after the download had finished it was possible to launch any of the apps that were installed directly from the Dash without QTCreator loaded. I am still not having any success with the "type=mir" problem. Even "lightdm stop" followed by "lighdm start" does not make any difference. Still, at least I can use Nano to remove "type=mir" from the lightdm configuration file. I have been wondering why there is the instruction to restart lightdm. Finally worked out the reason. It is simply like logging out and logging back in.


SDK .. Ahahahahehe ...:)  That really made my day :) Very simple. Nice

MIR... I think it all has to do with  a certain driver version on ATi graphics cards... but I agree .. it is like logging in and logging out. I am still very enthusiastic about it and will keep on trying different things as it rolls out. Of course I will post any developments here.

Regards,

Ventrical

---

### Post by bcbc on 2013-03-22
> **ventrical said:**
> Tried everything. Removed PC from KVM, purged and re-installed mir/ppa.

type=mir still gives me just gives me black-screen. Perhaps those tests are run in a cadence controlled environment.

I asked on #ubuntu-mir on IRC. I'm getting the black screen as well. This is the response:
> 
21:56 < bcbc2> Running mir ppa on Raring. When I add type=mir to lightdm.conf I 
               get a terminal login. This is the lightdm.log: 
               [http://paste.ubuntu.com/5636106/](http://paste.ubuntu.com/5636106/) Any ideas? PS the 
               mir_egltriangle runs correctly in the separate test
21:59 < RAOF> bcbc2: XMir currently isn't in the PPA, so those steps won't work.
22:00 < bcbc2> RAOF: ah ok. So I need to compile from source? 
22:00 < RAOF> bcbc2: XMir & the associated drivers will land after I've landed 
              [https://code.launchpad.net/~raof/mir/use-dma-buf/+merge/153267](https://code.launchpad.net/~raof/mir/use-dma-buf/+merge/153267) 
              and the associated changes.
22:02 < RAOF> bcbc2: Yeah, you can build from source if you want; the necessary 
              code is on github - [https://github.com/RAOF/xserver](https://github.com/RAOF/xserver) and the 
              associated driver from xf86-video-{ati,intel,nouveau}
22:02 < RAOF> (Note, I don't think nouveau's currently working)
22:02 < RAOF> bcbc2: It's pretty boring, too (as long as it works) - everything 
              looks exactly like it currently does, with the exception that 
              colour management doesn't work :)



---

### Post by ventrical on 2013-03-22
> **bcbc said:**
> I asked on #ubuntu-mir on IRC. I'm getting the black screen as well. This is the response:


Thanks for that information .

 My problem is that nano keeps destroying my mir.log and lighdm.log is always overwrote on login. I will have to redo my experiment over again where there was information in mir.log told me that I had the wrong version of video driver (1.8 or somthing and needed 2.3) but this only worked on ATI. I get all the demos just fine on Nvidia-nouveau, Ati and Intel graphics but type=mir does not bring  to Ubuntu Desktop. Perhaps this is not what the author meant because I can run mir from tty1  then htop.  Mir will be in htop. Also mir will continue to run in the background until you F9 in htop and choose 'kill'.  However if you do not kill mir first before switching to F7 you will loose your desktop and reboot required.

---

### Post by ventrical on 2013-03-23
mircommon-dev now in repos.

---

### Post by zika on 2013-03-23
> **ventrical said:**
> mircommon-dev now in repos.What does it bring new? I've seen it yesterday but did not have time/urge to do anything with it... What can be done with it?

---

### Post by ventrical on 2013-03-23
> **zika said:**
> What does it bring new? I've seen it yesterday but did not have time/urge to do anything with it... What can be done with it?

The last batch of updates killed everything here .. so far. No demos will work .. etc.. (intel Graphics).
Edit:

 Killed mir_demo_actions on  my *updated*  Nvidia installs also.

  I expected this..

Will check up on ATi install.

Edit:

Mir_demos on ATI install still works ok after updates. I'm not sure what happened. as for mircommon-dev. I think it does nothing right now. I just thought I would let everyone know it was there. I mean .. to be frank about it , it appears that Mir  is nothing more than  left over fumes of wayland/weston gone by atm but I think it will come alive soon :)

regards,

Venrtrical

---

### Post by grahammechanical on 2013-03-23
I think that someone reacted to the complaints that the skunks works project was a secretive conspiracy and has let a couple of skunks loose. Projects like this were supposed to be revealed when they were finished and polished. But then again, if the Raring code branch really does go rolling on and on, stuff like this would have come down during daily updates at some time in the future. And here we are ready and waiting.

Regards.

---

### Post by ventrical on 2013-03-23
With a major rewrite and infrastructure injection I would expect that these things would happen early and often, (better than never or later).  I hope the devs are eyeballing this forum, elst, they will  become insular as their most imediate predeccessor and it will most likely be a scratch for older desktops and those older ironworks will be seconded to some reasonable facsimile of a forked over Unity 2D desktop, Mate or a manintained X windowing system with a legacy Unity 3D.  More and more the testing options are being corralled into cadence testing because cadence testing is reliable to developers because it basically tells them what they want to hear and if there is an anomoly here an there then they can flag it as a hybrid  problem that was blacklisted, obsoleted or discontinued.

  . <see below off a cold boot with no mir instance>.

---

### Post by ventrical on 2013-03-23
Interesting. On one of my machines with ATi Radeon 1200x series I was able to use type-mir in the lightdm.conf file and even reboot into that file. Lightdm did not come up (black screen with blinking cursor) but I got all my terminals working. I was able to switch back to different terminals and then remove type =mir with nano. While I was in tty1 I ran (sleep 5; mir_eglplasma) & mir ; kill $! and got the following. An inverted Ubuntu-Desktop with a slipt :)) Now things are getting interesting indeed :) lol

Edit:

 I just realized somthing . It may be nothing but in the morning I am going to try and set my screen resolution to a lower scale , experiment there and see what happens.

Edit:

Can't set resolution because display widget will not come up .. Wrong driver I think.

---

### Post by ventrical on 2013-03-23
I am not sure if I have the right driver for this graphics adapter. Any pointers on installing another one or a right one?

I ask here because I am having a small prob  testing mir in raring.

Thanks.

```

0000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RS690 [Radeon X1200 Series]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:47 memory:f0000000-f7ffffff memory:fdff0000-fdffffff ioport:de00(size=256) memory:fde00000-fdefffff

```

---

### Post by zika on 2013-03-24
> **zika said:**
> With which kernel and driver. "Nomodesset" was depreciated not so long ago... If You're u-to-date there might be no way of going nomodeset any more...
If You still need help how to change Grub, shout...I've stumbled on article that I've read some time ago and that is the article about final demise of nomodeset both for AMD and NVidia...
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2ODA](http://www.phoronix.com/scan.php?page=news_item&px=MTI2ODA)

---

### Post by grahammechanical on 2013-03-24
Let me see if I understand this correctly. When we add nomodeset to the boot parameters, then that is user-space mode-setting (UMS). And the ability to use user-space mode setting is being depreciated (not supported in future, even now). This is being done because ATI developers are confident that they have a system where the video mode can be accurately set in kernel-space (KMS). This would also apply to all the F6 options where newer ATI hardware and drivers are installed for they are all added in user-space.

So, we can have confidence that from now on when using newer ATI adapters with the latest ATI drivers, all Live Sessions will run as they should and all installations of Ubuntu will result in a working desktop after the reboot. All I can say is, everyone has my best wishes for the future. Oh, I better add, apologies to Richard Stallman. :)

Regards.

---

### Post by bcbc on 2013-03-24
If it's deprecated, why is it still included for recovery mode in grub.cfg? Someone didn't get the memo?

---

### Post by zika on 2013-03-24
> **bcbc said:**
> If it's deprecated, why is it still included for recovery mode in grub.cfg? Someone didn't get the memo?Obstruction by rascals among us... ;)
You can simply try that for yourself... ;)
See one of my previous posts above...
Radeon (as module/driver) still respect switch radeon.modeset=0, as noted in that same post and tried before that...
So, to conclude: it is not yet fully operational but it will be in 3.9 final... As far as I did comprehend respective &#8222;papers&#8220;...
There are much better places to complain about that decision than here... ;)

---

### Post by bcbc on 2013-03-24
nomodeset still works for me...

---

### Post by zika on 2013-03-24
> **bcbc said:**
> nomodeset still works for me...If it is ATI at Your place, I stand corrected...

---

### Post by bcbc on 2013-03-24
I have an intel card.

---

### Post by zika on 2013-03-24
> **bcbc said:**
> I have an intel card.If You read my post that I mentioned and article that I gave URL for, You'll see that it is announced only for ATI and NVidia, as far as I've understood, and as I wrote...

---

### Post by bcbc on 2013-03-24
Maybe I should read that. zzzzz :)

OKay I'll go back on topic now.

---

### Post by grahammechanical on 2013-03-24
Depreciate = a) to lower, diminish the value of; b) to undervalue, disparage, make little of; c) to decline in market value, or in price; to loose quality, or efficiency, as through hard wear.

Why software developers should use this word to mean that they will no longer develop some code, or keep it up to date but will let it fall out of use, I do not know. But I do not think that it means that all of a sudden these F6 options will stop working on machines that have non-latest hardware. I do think that at some time in the future the F6 options may not be of any use and should be removed from the Installer. Of course, I may be wrong about this. Completely wrong. But I think we are seeing on this forum (other sections) posts where people are saying that they tried nomodeset and they still get a black screen.

---

### Post by bcbc on 2013-03-24
It should be deprecate. I suspect someone made a typo somewhere

---

### Post by ventrical on 2013-03-24
> **ventrical said:**
> Interesting. On one of my machines with ATi Radeon 1200x series I was able to use type-mir in the lightdm.conf file and even reboot into that file. Lightdm did not come up (black screen with blinking cursor) but I got all my terminals working. I was able to switch back to different terminals and then remove type =mir with nano. While I was in tty1 I ran (sleep 5; mir_eglplasma) & mir ; kill $! and got the following. An inverted Ubuntu-Desktop with a slipt :)) Now things are getting interesting indeed :) lol

Edit:

 I just realized somthing . It may be nothing but in the morning I am going to try and set my screen resolution to a lower scale , experiment there and see what happens.

Edit:

Can't set resolution because display widget will not come up .. Wrong driver I think.


 Update:

 I had to remove my NVidia GeForce 218/210 graphics adapter to enable the 'display' tool to work from settings in raring. So Now I can again experiemnt to see if I can get Mir to work with 'type=mir' in lightdm.conf.

---

### Post by ventrical on 2013-03-24
> **bcbc said:**
> It should be deprecate. I suspect someone made a typo somewhere

Deprecate is synonymous with depreciate.

---

### Post by bcbc on 2013-03-24
If by synonymous you mean completely different ;)

---

### Post by ventrical on 2013-03-24
> **bcbc said:**
> If by synonymous you mean completely different ;)

the same...

[http://en.wikipedia.org/wiki/Synonym](http://en.wikipedia.org/wiki/Synonym)

---

### Post by ventrical on 2013-03-24
> **ventrical said:**
> Interesting. On one of my machines with ATi Radeon 1200x series I was able to use type-mir in the lightdm.conf file and even reboot into that file. Lightdm did not come up (black screen with blinking cursor) but I got all my terminals working. I was able to switch back to different terminals and then remove type =mir with nano. While I was in tty1 I ran (sleep 5; mir_eglplasma) & mir ; kill $! and got the following. An inverted Ubuntu-Desktop with a slipt :)) Now things are getting interesting indeed :) lol

Edit:

 I just realized somthing . It may be nothing but in the morning I am going to try and set my screen resolution to a lower scale , experiment there and see what happens.

Edit:

Can't set resolution because display widget will not come up .. Wrong driver I think.

Followup:

 I was able to set display from <settings. but to no avail to get Mir to work in raring in any sense .

---

### Post by bcbc on 2013-03-24
> **ventrical said:**
> the same...

[http://en.wikipedia.org/wiki/Synonym](http://en.wikipedia.org/wiki/Synonym)
Yes I know what synonomous means. 

[http://english.stackexchange.com/a/45296](http://english.stackexchange.com/a/45296)
> *Deprecated*[COLOR=#393318][FONT=Georgia] is normally used today for some feature of a computer language which is still supported, but no longer recommended. It may [/FONT][/COLOR]*not*[COLOR=#393318][FONT=Georgia] be supported at some time in the future, because it doesn't fit well with the way the language is being developed.[/FONT][/COLOR]

Edit: Also [http://en.wikipedia.org/wiki/Deprecation](http://en.wikipedia.org/wiki/Deprecation)

---

### Post by ventrical on 2013-03-24
@grahammechanical

  The most recent updates allowed me to run that 'mir & htop'  tty1 with a lot better functioning. This time it loaded , ran high in the CPU then dropped back down. With the nvidia/nouveau you have to do that  little switch ... to CTRL+ALT+F7 .. then ESC .... then back to CTRL+ALT+F1 .. and you can quit Htop and run the 'mir & htop' again with no prob, but loose lightdm logon until reboot.

 For what it is worth .. you can see 'R' for MIR running in raring !!

regards..

---

### Post by cecilpierce on 2013-03-25
Is it possible to run mir ix Xubuntu ?

Here is what I have in lightdm.conf:
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
type=mir

#[SeatDefaults]
#user-session=ubuntu
#greeter-session=unity-greeter
#type=mir

Get black screen and blinking cursor but in a tty ps aux | grep mir says its running ?
 Tried both "SeatDefaults", same thing.

---

### Post by zika on 2013-03-25
> **bcbc said:**
> It should be deprecate. I suspect someone made a typo somewhereIt might as well be me... I do doubt because I did not quote, but... ;)
Whatever, I'm sure what the future will bring to „nomodeset“... ;)

---

### Post by zika on 2013-03-25
> **ventrical said:**
> Deprecate is synonymous with depreciate.In Mir-language?

---

### Post by ventrical on 2013-03-25
> **zika said:**
> In Mir-language?


  I  am just not sure that this was the content in which grahammechanical was trying to describe it. They both basically mean the same thing .. something that looses it's value and no attention is paid to it.  No offence to you at all .. but I wonder why we are veering to phonics discussion ! :)

---

### Post by ventrical on 2013-03-25
> **cecilpierce said:**
> Is it possible to run mir ix Xubuntu ?

Here is what I have in lightdm.conf:
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
type=mir

#[SeatDefaults]
#user-session=ubuntu
#greeter-session=unity-greeter
#type=mir

Get black screen and blinking cursor but in a tty ps aux | grep mir says its running ?
 Tried both "SeatDefaults", same thing.


Then it is running!   I just think that there may have been a misunderstanding at present that it would run the ubuntu-desktop. Hey ..at this point. any instance of mir is worth reporting! .
Thanks!

---

### Post by zika on 2013-03-25
> **ventrical said:**
> Then it is running!   I just think that there may have been a misunderstanding at present that ti would run the ubuntu-desktop. **Hey ..at this point. any instance of mir is worth reporting! .**
Thanks![B]Hallelujah
[/B]**JOYOUS CELEBRATION**

[http://www.youtube.com/watch?v=1s1LJbzRulM](http://www.youtube.com/watch?v=1s1LJbzRulM)
[http://www.youtube.com/watch?v=YrLk4vdY28Q](http://www.youtube.com/watch?v=YrLk4vdY28Q)

---

### Post by ventrical on 2013-03-25
> **zika said:**
> [b]hallelujah
[/b]**joyous celebration**

[http://www.youtube.com/watch?v=1s1ljbzrulm](http://www.youtube.com/watch?v=1s1ljbzrulm)
[http://www.youtube.com/watch?v=yrlk4vdy28q](http://www.youtube.com/watch?v=yrlk4vdy28q)

rotflmao!! :)

---

### Post by cecilpierce on 2013-03-25
Verry good, "JOYOUS CELEBRATION 13 - UCHE - MY GOD IS GOOD".
Thanks
[http://www.youtube.com/watch?v=yrlk4vdy28q](http://www.youtube.com/watch?v=yrlk4vdy28q) says unavailable

---

### Post by zika on 2013-03-25
> **cecilpierce said:**
> Verry good, "JOYOUS CELEBRATION 13 - UCHE - MY GOD IS GOOD".
Thanks
[http://www.youtube.com/watch?v=yrlk4vdy28q](http://www.youtube.com/watch?v=yrlk4vdy28q) says unavailable
[http://www.youtube.com/watch?v=YrLk4vdY28Q](http://www.youtube.com/watch?v=YrLk4vdY28Q)
Copy and paste got stuck in Mir...

---

### Post by cecilpierce on 2013-03-25
@zika

Got it, thanks.

---

### Post by ventrical on 2013-03-26
> **zika said:**
> [http://www.youtube.com/watch?v=YrLk4vdY28Q](http://www.youtube.com/watch?v=YrLk4vdY28Q)
Copy and paste got stuck in Mir...


  Lots of updates .. but still no functional mir. I really do not get the connection of the link .. and once I do , I'll answer .. be sure..

---

### Post by zika on 2013-03-26
> **ventrical said:**
> Lots of updates .. but still no functional mir. I really do not get the connection of the link .. and once I do , I'll answer .. be sure..I'm glad that copy&paste works for You even in Mir... [http://ubuntuforums.org/showthread.php?t=2129432&p=12574900#post12574900](http://ubuntuforums.org/showthread.php?t=2129432&p=12574900#post12574900) ...
You asked me a silent question. Let me answer it... Look at the name of the song and You might get it... ;)
[http://ubuntuforums.org/showthread.php?t=2125215&p=12572820#post12572820](http://ubuntuforums.org/showthread.php?t=2125215&p=12572820#post12572820) gave me a false impression that You've got it...

---

### Post by ventrical on 2013-03-26
> **zika said:**
> I'm glad that copy&paste works for You even in Mir... [http://ubuntuforums.org/showthread.php?t=2129432&p=12574900#post12574900](http://ubuntuforums.org/showthread.php?t=2129432&p=12574900#post12574900) ...
You asked me a silent question. Let me answer it... Look at the name of the song and You might get it... ;)
[http://ubuntuforums.org/showthread.php?t=2125215&p=12572820#post12572820](http://ubuntuforums.org/showthread.php?t=2125215&p=12572820#post12572820) gave me a false impression that You've got it...




> **zika said:**
> I'm glad that copy&paste works for You even in Mir...

I don't get why you have to slight me about mir. I  can take a joke  but  this is a lot of volunteer work here. I tried to return the favor  [http://ubuntuforums.org/showthread.php?t=2129432&p=12574768#post12574768](http://ubuntuforums.org/showthread.php?t=2129432&p=12574768#post12574768) but it appears  that it rubbed you the wrong way.

 Hey .. I'm just trying to test the best that I can ..not to rub you the wrong way ... but to beta test mir .

---

### Post by zika on 2013-03-26
> **ventrical said:**
> I don't get why you have to slight me about mir. I  can take a joke  but  this is a lot of volunteer work here. I tried to return the favor  [http://ubuntuforums.org/showthread.php?t=2129432&p=12574768#post12574768](http://ubuntuforums.org/showthread.php?t=2129432&p=12574768#post12574768) but it appears  that it rubbed you the wrong way.

 Hey .. I'm just trying to test the best that I can ..not to rub you the wrong way ... but to beta test mir .I think You completely misunderstood me, I think... I'll take that completely on me and stop any further discussion... Let me say: Mea culpa and that is it... I tried to help in testing whatever is present of Mir yet, but... I'll just say: Mir, brother... ;) Without any rubbing, please...

---

### Post by ventrical on 2013-03-26
> **zika said:**
> I think You completely misunderstood me, I think... I'll take that completely on me and stop any further discussion... Let me say: Mea culpa and that is it... I tried to help in testing whatever is present of Mir yet, but... I'll just say: Mir, brother... ;) Without any rubbing, please...


Yes .. I did misunderstand you .  You not a culpa .. mea culpa !:)  Please .. say whatever you want about mir ..   it's currently a horror in it's current state but ..ya know .. what are we going to do at this stage of the game ?? Plea with Mark S.  to not implement Mir and go back to walyland/weston ??? or just stick with X??  I know .. . I know.. there is always archlinux and slackware and a gazzilion other distros  .  I first started my PC science carreer at Norfolk &Western Railway in Detroit Mi learning how the IBM UniVax punch card machine  would line up box cars or railway tracks in rows and colums - sort of like a real life matrix .. I was 11 years old. My programming career started with pinball machines. (I used to maintain a device called the game_mech) and all the operations were controlled by resetting the game mech and setting these switches, all relay controlled. and from there  on  to old space invader games. So , if it seems like I am a dinosaur to Ubuntu or Linux .. then .. E'll yes .. I am :) but I gotta keep moving on to cutting edge stuff because I just get bored really easy .. and nobody should  have to feel intimidated just because I 'm bored.


 Whatever the case .. I think  the Ubuntu community  is stuck with mir .. so my line of approach is to attack it as often as I can .. offer what I can to make it better and get it rolling. I know that I will probably put my foot in my mouth more often that not and eat a lot of crow also but I honestly think it is worth the time. So  it is really up to us , all of us in the community. What we contribute  to testing mir in these early days may  make the difference of mir being a beautiful masterpiece or a complete failure.

Thanks for your time..

regards,
Ventrical

---

### Post by ventrical on 2013-03-26
Was able to "this bug affects me too".

 
[https://bugs.launchpad.net/mir/+bug/1109957](https://bugs.launchpad.net/mir/+bug/1109957)

---

### Post by Gyokuro on 2013-03-26
> **ventrical said:**
> Yes .. I did misunderstand you .  You not a culpa .. mea culpa !:)  Please .. say whatever you want about mir ..   it's currently a horror in it's current state but ..ya know .. what are we going to do at this stage of the game ?? Plea with Mark S.  to not implement Mir and go back to walyland/weston ??? or just stick with X??  I know .. . I know.. there is always archlinux and slackware and a gazzilion other distros  .  I first started my PC science carreer at Norfolk &Western Railway in Detroit Mi learning how the IBM UniVax punch card machine  would line up box cars or railway tracks in rows and colums - sort of like a real life matrix .. I was 11 years old. My programming career started with pinball machines. (I used to maintain a device called the game_mech) and all the operations were controlled by resetting the game mech and setting these switches, all relay controlled. and from there  on  to old space invader games. So , if it seems like I am a dinosaur to Ubuntu or Linux .. then .. E'll yes .. I am :) but I gotta keep moving on to cutting edge stuff because I just get bored really easy .. and nobody should  have to feel intimidated just because I 'm bored.


 Whatever the case .. I think  the Ubuntu community  is stuck with mir .. so my line of approach is to attack it as often as I can .. offer what I can to make it better and get it rolling. I know that I will probably put my foot in my mouth more often that not and eat a lot of crow also but I honestly think it is worth the time. So  it is really up to us , all of us in the community. What we contribute  to testing mir in these early days may  make the difference of mir being a beautiful masterpiece or a complete failure.

Thanks for your time..

regards,
Ventrical

Looking at all your posts it seems you are investing a lot of time to test MIR however I think it is better to check from time to time what is in the MIR repo and test later in case all necessary pieces are in. Without XMIR you are not able to test X-applications and you will need MIR support patches for GTK/QT to test applications which make use of previous mentioned toolkits - all this patches are not available yet. Looking at wayland the support patches are already in QT and GTK but as long Gnome is not ported to use Wayland you can test only some Gnome applications. 

[http://www.phoronix.com/scan.php?page=news_item&px=MTMzNjM](http://www.phoronix.com/scan.php?page=news_item&px=MTMzNjM)
[https://live.gnome.org/Wayland](https://live.gnome.org/Wayland)

for the moment Wayland is far ahead due to very good engineering work of the X developers as they have done the ground work in the past.  I think some people have to realize that you can not patch and port all this software projects overnights and say mission accomplished in 6 months. For the moment X11 is good enough and if MIR do not take off there is wayland which is the scheduled successor of X11. Upstream developers and project maintainers are aware of this and do their best so that this can happen.

---

### Post by ventrical on 2013-03-26
That is a great fall-back strategy if Mir ultimately fails.  Ubuntu , and most of the Linuxses , all have these fallback features. I am to understand that  mir will talk to x and wayland etc.. so perhaps they will all get along. Not only do we have choice of Ubuntu flavours but choice of display servers.

 For now I have X which meets all services and then some .. so there are no complaints from me. If compiz and ccsm fail in Raring  then I have no problem locking Lucid Lynx and running a customized version of Ubuntu on my big machines. In front of me, leaning on one of my KVM units I have the 4th Edition of Running Linux 2002. Matt Welsh .. etc.. and it is rather outdated. I like moving on to new things. I gave wayland a good try and then it just stopped progressing. Maybe it's just me. Anyways .. one of my jobs in my early career (before floppies and hdds) was to disassemble  mechanical relay modules, troubleshoot them , test them , repair them and reassemble them. They were just basically small units of a total larger unit. When Microprocessors first came out I troubleshooted VAGs for cold solder joints. Part of my expertise way back then was to find microfractures in seemingly good solder joints that were acting as circuit breaks. Even as the PC revolution took off I still  repaired MoBo and inspected them for cold solder joints. I still do this to this day!!

 I like doing the same thing with blocks of code. The 'mir' executable in /usr/bin/ is a small block of code that makes calls on many other objects and components. I like to disassemble  all these things. Why ?  It's just what I do. I think to myself that perhaps I might ask a question or contribute somthing to make mir better or move along .. or maybe somebody will come up with even a better alternative. 

  I think I stated before in another forum that  my eyesight is becoming diminished with age. The Unity desktop in current Ubuntu gives my eyes a soothing effect unlike other desktops. I am not sure I want to spend too much time trying other desktops (as I have experimented with quite a few already). So that brings me here, hoping that 'mir' will succeed and hence also Unity. The wayland team is big enough. No? So why should I spend time disassembling wayland when I can disassemble mir?

  However .. you bring some good points to the table to be considered definitely.

---

### Post by Gyokuro on 2013-03-27
> **ventrical said:**
> That is a great fall-back strategy if Mir ultimately fails.  Ubuntu , and most of the Linuxses , all have these fallback features. I am to understand that  mir will talk to x and wayland etc.. so perhaps they will all get along. Not only do we have choice of Ubuntu flavours but choice of display servers.

 For now I have X which meets all services and then some .. so there are no complaints from me. If compiz and ccsm fail in Raring  then I have no problem locking Lucid Lynx and running a customized version of Ubuntu on my big machines. In front of me, leaning on one of my KVM units I have the 4th Edition of Running Linux 2002. Matt Welsh .. etc.. and it is rather outdated. I like moving on to new things. I gave wayland a good try and then it just stopped progressing. Maybe it's just me. Anyways .. one of my jobs in my early career (before floppies and hdds) was to disassemble  mechanical relay modules, troubleshoot them , test them , repair them and reassemble them. They were just basically small units of a total larger unit. When Microprocessors first came out I troubleshooted VAGs for cold solder joints. Part of my expertise way back then was to find microfractures in seemingly good solder joints that were acting as circuit breaks. Even as the PC revolution took off I still  repaired MoBo and inspected them for cold solder joints. I still do this to this day!!

 I like doing the same thing with blocks of code. The 'mir' executable in /usr/bin/ is a small block of code that makes calls on many other objects and components. I like to disassemble  all these things. Why ?  It's just what I do. I think to myself that perhaps I might ask a question or contribute somthing to make mir better or move along .. or maybe somebody will come up with even a better alternative. 

  I think I stated before in another forum that  my eyesight is becoming diminished with age. The Unity desktop in current Ubuntu gives my eyes a soothing effect unlike other desktops. I am not sure I want to spend too much time trying other desktops (as I have experimented with quite a few already). So that brings me here, hoping that 'mir' will succeed and hence also Unity. The wayland team is big enough. No? So why should I spend time disassembling wayland when I can disassemble mir?

  However .. you bring some good points to the table to be considered definitely.

What you have done in the past and doing now is interesting and it keeps you busy, your brain young and in the loop :-). Concerning your eyesight I think the Ubuntu fonts which get used as default fonts in unity are much more friendly to your eyes as the Gnome 3 default font (Cantarell). Everyone should do what is the best for him/her and in your case your MIR adventure - in any case you have your fun and learn something new.

---

### Post by balloons on 2013-03-27
Just dropping in to say I'm glad to see you all already diving in on this stuff :-) For now go ahead and tinker and report bugs, successes/failures, etc. As things shape up, we will certainly have some testing events around this -- I know you all will hammer on it in a good way when it's time!

---

### Post by ventrical on 2013-03-27
Hi Nick,

 I had read this here - [http://en.wikipedia.org/wiki/Mir_%28display_server%29](http://en.wikipedia.org/wiki/Mir_%28display_server%29)

which in part states:

"

[LIST]
[*]**October 2013** – Unity Next and Mir window management are  completely integrated with the rest of the system to support an Ubuntu  Phone product. Desktops and laptops will have access to a legacy mode  that allows to run legacy X clients against an on-demand rootless X  server. "
[/LIST]
  

So does this mean that Mir will basically be unusable for current desktops up unto and after Oct. 2013 or is this information wrong or outdated.?

Thanks , 
Regards,
Ventrical

---

### Post by cecilpierce on 2013-03-27
Mir progress vid:
[http://www.youtube.com/watch?v=7grEFrTBzus&feature=youtu.be](http://www.youtube.com/watch?v=7grEFrTBzus&feature=youtu.be)
Looks like the irc channel is picking up...:P

---

### Post by ventrical on 2013-03-28
Robert Ancell wrote;

> 
Dale, you appear to have a bug in your lightdm.conf:
"Failed to load configuration from /etc/lightdm/lightdm.conf: Key file contains line 'type-mir' which is not a key-value pair, group, or comment"

 Anybody have any ideas how to fix a buggy lightdm.conf ?

---

### Post by zika on 2013-03-28
> **ventrical said:**
> Robert Ancell wrote: [COLOR=#000000]*Dale, you appear to have a bug in your lightdm.conf:*[/COLOR][COLOR=#000000][I]"Failed to load configuration from /etc/lightdm/lightdm.conf: Key file contains line 'type-mir' which is not a key-value pair, group, or comment"


[/I]
[/COLOR]
[COLOR=#000000][/COLOR]Anybody have any ideas how to fix a buggy lightdm.conf ?What is buggy in it?
If You have line```
type-mir
```in it, You shouldn't... Line should be```
type=mir
```...

---

### Post by ventrical on 2013-03-28
@zika 

Hey .. thanks zika.  Hawk-eyes as usual :) Typo me bad ..

  I think there are more problems though with  some of my setup.  Perhaps you  could look at the log files and see it you can make any sense of them ?

Thanks.

[https://bugs.launchpad.net/mir/+bug/1109957](https://bugs.launchpad.net/mir/+bug/1109957)

---

### Post by zika on 2013-03-28
> **ventrical said:**
> @zika 

Hey .. thanks zika.  Hawk-eyes as usual :) Typo me bad ..

  I think there are more problems though with  some of my setup.  Perhaps you  could look at the log files and see it you can make any sense of them ?

Thanks.

[https://bugs.launchpad.net/mir/+bug/1109957](https://bugs.launchpad.net/mir/+bug/1109957)As soon as I find spare time...
Update&#8321;: How come two persons with different names (none of them is ventrical) have the same (ventrical) folder on their machines? I might have missread something because it is difficult to differentiate reading bug reports You've pointed me to between two things: what is wrong with lightdm (if any) and what is inflicted (if any) by Mir...

---

### Post by ventrical on 2013-03-28
@zika,

 It would be this one here:

[https://bugs.launchpad.net/mir/+bug/1109957/comments/3](https://bugs.launchpad.net/mir/+bug/1109957/comments/3)

and yes .. I entered two messages because I have several different lightdm.logs created under  different conditions. It might be important to note that during progressive upgrade process from the mir ppa there have since been different scenarios presenting themselves. ie; Mir_demos will work, mir_demos will not work, mir_demos will work with corrupt screens, blank screens and no terminal, plymouth will work, can get terminal but will not boot into lighdm .. etc

 Please , take your time at your convenience.

---

### Post by zika on 2013-03-28
> **ventrical said:**
> @zika,

 It would be this one here:

[https://bugs.launchpad.net/mir/+bug/1109957/comments/3](https://bugs.launchpad.net/mir/+bug/1109957/comments/3)

and yes .. I entered two messages because I have several different lightdm.logs created under  different conditions. It might be important to note that during progressive upgrade process from the mir ppa there have since been different scenarios presenting themselves. ie; Mir_demos will work, mir_demos will not work, mir_demos will work with corrupt screens, blank screens and no terminal, plymouth will work, can get terminal but will not boot into lighdm .. etc

 Please , take your time at your convenience.

Machine:

```

ventrical@ventrical-PY028AA-ABA-A1106N:~$ gksu gedit
ventrical@ventrical-PY028AA-ABA-A1106N:~$ lshw
WARNING: you should run this program as super-user.
ventrical-py028aa-aba-a1106n
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1248MiB
     *-cpu:0
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          size: 3050MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          size: 3050MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfe80000-cfefffff ioport:b800(size=8) memory:d0000000-dfffffff memory:cfe40000-cfe7ffff
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:41 memory:cfe38000-cfe3bfff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:50000000-501fffff ioport:50200000(size=2097152)
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:a400(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:a800(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b000(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:b400(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:cfe37c00-cfe37fff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=8192) memory:cff00000-cfffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:20 memory:cffff800-cfffffff ioport:e800(size=128)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:13:d4:7c:9f:5a
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.14 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:21 ioport:e400(size=256) memory:cffff400-cffff4ff
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: LSI Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: latency=64 maxlatency=14 mingnt=236
                resources: memory:cff00000-cff000ff ioport:e000(size=8) ioport:d800(size=256)
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:a000(size=8) ioport:9800(size=4) ioport:9400(size=8) ioport:9000(size=4) ioport:8800(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVDRRW GWA-4166B
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1823
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 

```
This not HW-related so no use of the stuff You've dumped here...
No usable info, at least for me...
You've mentioned two dosens of cases but no hint what is really wrong...
What have You changed with that gedit command?
What command relate to which log?
What happens with each set of Mir commands? Take Your time, it seems that this is going to be a new run around the same circle...

---

### Post by ventrical on 2013-03-28
1.What have You changed with that gedit command?

Only 'type=mir' and then use gedit or nano to remove 'type=mir'. There is no problem there.  I only made typo 'type-mir' once so that bug report will be ammended.

2.What command relate to which log?

The lightdm.log takes no command to make. I use gksu gedit to view those logs in /var/log/upstart/lightdm.log.#.gz as suggested here:  [https://bugs.launchpad.net/mir/+bug/1109957/comments/1](https://bugs.launchpad.net/mir/+bug/1109957/comments/1)

---

### Post by ventrical on 2013-03-28
3. What happens with each set of Mir commands? Take Your time, it seems  that this is going to be a new run around the same circle...         

Currently with updated machine , all commands give me the following apport errors;..etc.. after running the code"

```

(sleep 3; _dem-_name_here) & mir ; kill $!

```

---

### Post by zika on 2013-03-28
> **ventrical said:**
> 3. What happens with each set of Mir commands? Take Your time, it seems  that this is going to be a new run around the same circle...         

Currently with updated machine , all commands give me the following apport errors;..etc.. after running the code"
You must be the favourite customer to the guys at the other side of that apport line...

---

### Post by ventrical on 2013-03-28
> **zika said:**
> This not HW-related so no use of the stuff You've dumped here...
No usable info, at least for me...
You've mentioned two dosens of cases but no hint what is really wrong..


Umm.. simply  after the  recent upgrades the demos will not work. Also 'type=mir' will not work.

> 


Take Your time, it seems that this is going to be a new run around the same circle... 		


?

---

### Post by balloons on 2013-03-28
> **ventrical said:**
> Hi Nick,

 I had read this here - [http://en.wikipedia.org/wiki/Mir_%28display_server%29](http://en.wikipedia.org/wiki/Mir_%28display_server%29)

which in part states:

"

[LIST]
[*]**October 2013** – Unity Next and Mir window management are  completely integrated with the rest of the system to support an Ubuntu  Phone product. Desktops and laptops will have access to a legacy mode  that allows to run legacy X clients against an on-demand rootless X  server. "
[/LIST]

So does this mean that Mir will basically be unusable for current desktops up unto and after Oct. 2013 or is this information wrong or outdated.?

Thanks , 
Regards,
Ventrical

Not sure where the wikipedia article is getting it's source ;-) Best to follow along with the actual development from the team -- they're giving weekly updates:

[https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html](https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html)
[https://lists.ubuntu.com/archives/mir-devel/2013-March/000022.html](https://lists.ubuntu.com/archives/mir-devel/2013-March/000022.html)

That said, the stated goal is to have MIR power the phone and desktop in lieu of X or something else for the phone. As far as when it will be usable on desktops, I don't have a definitive timeline; and of course it depends on what you mean 'usable'. This is all leading up to 14.04 when we want to have the converged device story all good. So mir+unity next should be running everywhere.

---

### Post by zika on 2013-03-28
> **ventrical said:**
> ?You should give those guys working on Mir a week or two to make something new and then we could test it... It seems You'e pushing them more than their „bosses“ if they have such in this FLOSS architecture...
Kernels do not get developed that fast...

---

### Post by ventrical on 2013-03-28
> **zika said:**
> You must be the favourite customer to the guys at the other side of that apport line...

;)

---

### Post by ventrical on 2013-03-28
> **zika said:**
> You should give those guys working on Mir a week or two to make something new and then we could test it... It seems You'e pushing them more than their „bosses“ if they have such in this FLOSS architecture...
Kernels do not get developed that fast...


 I agree .. thanks.

---

### Post by ventrical on 2013-03-28
> **guitara said:**
> Not sure where the wikipedia article is getting it's source ;-) Best to follow along with the actual development from the team -- they're giving weekly updates:

[https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html](https://lists.ubuntu.com/archives/mir-devel/2013-March/000005.html)
[https://lists.ubuntu.com/archives/mir-devel/2013-March/000022.html](https://lists.ubuntu.com/archives/mir-devel/2013-March/000022.html)

That said, the stated goal is to have MIR power the phone and desktop in lieu of X or something else for the phone. As far as when it will be usable on desktops, I don't have a definitive timeline; and of course it depends on what you mean 'usable'..

  Ok .. thanks Nick very much. This is very helpful.

Regrads,
Ventrical

---

### Post by ventrical on 2013-03-28
Most recent upgrade and now all demos are working again.

[http://www.youtube.com/watch?v=76RrdwElnTU](http://www.youtube.com/watch?v=76RrdwElnTU)

---

### Post by tad1073 on 2013-03-28
I've been following this thread since the beginning; tried mir twice to no avail, well the first time I tried it I didn't uninstall my nvidia driver and everything was in slow motion...lol...and it took me about 2 hours to get my machine back to the way I had it. The second time I tried it (with type=mir and sleep 3; _dem-_name_here & mir ; kill $!) I couldn&#8217;t get a desktop.

---

### Post by ventrical on 2013-03-29
> **grahammechanical said:**
> Depreciate = a) to lower, diminish the value of; b) to undervalue, disparage, make little of; c) to decline in market value, or in price; to loose quality, or efficiency, as through hard wear.

Why software developers should use this word to mean that they will no longer develop some code, or keep it up to date but will let it fall out of use, I do not know. But I do not think that it means that all of a sudden these F6 options will stop working on machines that have non-latest hardware. I do think that at some time in the future the F6 options may not be of any use and should be removed from the Installer. Of course, I may be wrong about this. Completely wrong. But I think we are seeing on this forum (other sections) posts where people are saying that they tried nomodeset and they still get a black screen.


  I had just discovered (news to me) that using <nomodeset> will force a machine to llvmpipe. Please see:

[http://ubuntuforums.org/showthread.php?t=2130229](http://ubuntuforums.org/showthread.php?t=2130229)

  The reason I have been using <nomodeset> from my USB iso installs is because  the standard method was most often failing. Having zsynced yesterdays -i386 daily I can now install successfully and get the correct 'nouveau' driver which is important for experimenting with mir.  So I hope that is good news for Nick's team.

Regards, Ventrical

---

### Post by grahammechanical on 2013-03-29
That wikipedia article is making a partial quotation from the Ubuntu wiki MIR specification.

[https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec](https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec)

See Roadmap. I see three or four aims for October 2013.

a) Complete integration of Unity Next and Mir window management into the system on the Ubuntu phone product. 
b) Fully replace X in user sessions on the desktop/laptop as well as providing a legacy mode for x clients that have not yet caught up with the change to Mir on Ubuntu. 
c) The implementation of a cascade of display servers/shells to provide a flicker free, tightly integrated and beautiful User Experience (UX). 

I do not see any mention of anything being Awesome. A bit of a disappointment that is. :)

There is a lot of interesting stuff coming to the development branch. Unity 7 "wi a hundred pipers an' a' an' a'." Sorry that should be a hundred scopes. I could not resist saying it. Unity 7 to morph into Unity Next along with Mir being developed and then there are touch apps and other community developed apps. An interesting year ahead.

---

### Post by EgoGratis on 2013-03-31
Nobody testing Mir anymore? ;)

P.S. I have a feeling it will make more sense to test Mir on mobile devices this year and next year on the desktop but i could be wrong!

---

### Post by ventrical on 2013-03-31
> **EgoGratis said:**
> Nobody testing Mir anymore? ;)

P.S. I have a feeling it will make more sense to test Mir on mobile devices this year and next year on the desktop but i could be wrong!

I,m still at it. Holidays in Canada for the weekend.

---

### Post by EgoGratis on 2013-04-01
Ubuntu DE is progressing nicely and i might be wrong but i think this apps on mobile devices is what we will be testing the most this year regarding Mir:

[http://mhall119.com/2013/04/more-ubuntu-sdk-apps/](http://mhall119.com/2013/04/more-ubuntu-sdk-apps/)

---

### Post by ventrical on 2013-04-01
> **EgoGratis said:**
> Ubuntu DE is progressing nicely and i might be wrong but i think this apps on mobile devices is what we will be testing the most this year regarding Mir:

[http://mhall119.com/2013/04/more-ubuntu-sdk-apps/](http://mhall119.com/2013/04/more-ubuntu-sdk-apps/)


 Unity has become it's snappy , effervescent self once more.  I think we may all be surprised with how fast Mir progresses for the desktop  (or X/wayland fallbacks). I would expect major breakage in development branch after Raring final is released. So far .. nothing new at this end on my test machines .. and now I have other work so I am busy again.

---

### Post by grahammechanical on 2013-04-02
@ventrical

I have not yet seen this video. It is a Ubuntu On Air discussion by the developers about Mir and the next Unity.

[http://www.youtube.com/UbuntuOnAir](http://www.youtube.com/UbuntuOnAir)

It is only now being posted to youtube. So, we need to give them so time to set things up.

Regards.

---

### Post by EgoGratis on 2013-04-02
[B]*UnityNext & Mir Weekly Report**
*Mar 29, 2013*[/B]

[https://lists.ubuntu.com/archives/mir-devel/2013-March/000052.html](https://lists.ubuntu.com/archives/mir-devel/2013-March/000052.html)

**Building UnityNext**

[http://unity.ubuntu.com/getinvolved/development/unitynext/](http://unity.ubuntu.com/getinvolved/development/unitynext/)

[Source]("http://www.iloveubuntu.net/unity-next-capable-running-desktop-windowed-app-started-move-towards-usable-stage")

P.S. UnityNext does not use Mir ATM but it might be fun to build for someone.

---

### Post by grahammechanical on 2013-04-02
That unity.ubuntu.com link says to build on 12.10 but another link from that page says this

> [COLOR=#333333][FONT=Ubuntu Beta]Images are currently built in the Canonical data center and they are based on [/FONT][/COLOR]quantal[COLOR=#333333][FONT=Ubuntu Beta]. Over the next days all necessary changes for Ubuntu Touch are going to go into Ubuntu [/FONT][/COLOR]raring[COLOR=#333333][FONT=Ubuntu Beta] and images will be built using [/FONT][/COLOR]raring[COLOR=#333333][FONT=Ubuntu Beta] as a basis.[/FONT][/COLOR]

The images referred to are for mobile touch devices but it encourages the hope that it will soon be possible to build Unity Next on Raring desktop. Which really is the way forward.

Some pics here and info

[http://www.omgubuntu.co.uk/2013/04/how-to-run-unity-next-on-your-desktop](http://www.omgubuntu.co.uk/2013/04/how-to-run-unity-next-on-your-desktop)

Regards.

---

### Post by cecilpierce on 2013-04-02
Tried it on raring, seem to go but something is missing.

Run the People Lens daemon to enable ‘contacts’ in your ~/unity/unity_build/libexec/unity-people-daemon, didn't see /libexec directory

---

### Post by EgoGratis on 2013-04-04
We will need to get mobile devices to test latest stuff desktop PC just doesn't cut it anymore. ;)

[http://www.iloveubuntu.net/unity-demoed-running-mir-nexus-4](http://www.iloveubuntu.net/unity-demoed-running-mir-nexus-4)

---

### Post by mc4man on 2013-04-04
> **cecilpierce said:**
> Tried it on raring, seem to go but something is missing.

Run the People Lens daemon to enable ‘contacts’ in your ~/unity/unity_build/libexec/unity-people-daemon, didn't see /libexec directory
If you didn't figure yet it's not quite the right path, more like ~/unity/unity_build/build/libexec/unity-people-daemon

Over all not much to do  with it, (as seen on a raring build), except pull/push new screens, launcher, ect. Looks just like a typical smart phone/tablet

---

### Post by ventrical on 2013-05-04
A day or so ago 'mir' and components got ripped out (removed) and now are being replaced again with todays update. I just thought I would make a note.

```

 appmenu-qt appmenu-qt5 aptitude aptitude-common bamfdaemon bc cpp-4.8 dc
  devscripts g++-4.8 gcc-4.8 gcc-4.8-base gir1.2-appindicator3-0.1
  gir1.2-messagingmenu-1.0 gir1.2-packagekitglib-1.0 gstreamer1.0-plugins-good
  gstreamer1.0-pulseaudio indicator-datetime indicator-messages
  indicator-session indicator-sound libappindicator1 libappindicator3-1
  libasan0 libatomic1 libbamf3-1 libdbusmenu-qt2 libdbusmenu-qt5 libdrm-dev
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libgcc-4.8-dev libgcc1
  libgomp1 libgstreamer-plugins-good1.0-0 libindicator3-7 libindicator7
  libitm1 libkms1 libmessaging-menu0 libmirclient-dev libmirclient0
  libmirprotobuf-dev libmirprotobuf0 libmirserver0 libquadmath0 libsqlite3-0
  libssh-4 libstdc++-4.8-dev libstdc++6 libtelepathy-logger3 libvisio-0.0-0
  libwpd-0.9-9 lintian mir-doc mircommon-dev packagekit
  packagekit-backend-aptcc packagekit-tools python-appindicator
  python3-pyatspi qtdeclarative5-ubuntu-ui-toolkit-plugin telepathy-gabble
  telepathy-indicator telepathy-logger ubuntu-sdk ubuntu-ui-toolkit-doc
  ubuntu-ui-toolkit-examples ubuntu-ui-toolkit-theme upstart
  zeroinstall-injector

```

---

### Post by cariboo on 2013-05-04
> **ventrical said:**
> A day or so ago 'mir' and components got ripped out (removed) and now are being replaced again with todays update. I just thought I would make a note.

<snip>

We are always going to see packages removed and replaced during the development cycle, this is nothing new. Perhaps it's time to start a new thread about Mir and Saucy.

---

### Post by ventrical on 2013-05-14
> **cariboo907 said:**
> We are always going to see packages removed and replaced during the development cycle, this is nothing new. Perhaps it's time to start a new thread about Mir and Saucy.

@Cariboo

  There is no way that I can get 'mir' executable to install without 'held broken packages' and removing libmirserver0 in the saucy salmander. So I'll have to do some rollbacks to raring and install and work  with Mir there. Since Mir is in development, can we not discuss that here?

Regards,

Ventrical

---

### Post by cariboo on 2013-05-14
> **ventrical said:**
> @Cariboo

  There is no way that I can get 'mir' executable to install without 'held broken packages' and removing libmirserver0 in the saucy salmander. So I'll have to do some rollbacks to raring and install and work  with Mir there. Since Mir is in development, can we not discuss that here?

Regards,

Ventrical

You're going to run into that, when you have the proposed repositories enabled, they are more or less being used to store packages, until all the dependencies have been built, and test have been passed.

---

### Post by jerrylamos on 2013-05-14
> **EgoGratis said:**
> We will need to get mobile devices to test latest stuff desktop PC just doesn't cut it anymore. ;)

[http://www.iloveubuntu.net/unity-demoed-running-mir-nexus-4](http://www.iloveubuntu.net/unity-demoed-running-mir-nexus-4)?  I've got ubuntu on netbook, notebook, desktop, also tablets 7" and 10" with android browser and 9" tablet with chrome browser.  These tablets are quite fast compared to ubuntu (ubuntu has the faster hardware) and mostly O.K. for output.  The tablets in my case are not so good to terrible for input.  I really don't have the hang for managing files and folders on them either.  In my case at my ability level ubuntu beats the tablets silly on versatility.  

For what functions the tablets will do they are more user friendly.  Example they immediately connect on my encrypted hidden network while every ubuntu since Precise requires manual input on every boot to connect.  Network manager tries to connect without using the password, doesn't work of course, then declares the network out of range and disconnects.  Systems settings > network > connect to hidden network > select the network > wait, wait, drop down shows it already knew the password, select, wait, connects, then close systems settings.  Yes there's a launchpad bug, no, development is not interested.  I boot a lot during testing.  In constrast the tablets and chromebook (I've got a chromebook too) "just work".

And no I'm not interested in putting my personal data (except selected pictures) up in some cloud for the target marketeers, spammers and hackers.

I'm not at all sure how to "test latest stuff" on Asus, Samsung, and Nook tablets.  I've looked at the posts on chrubuntu for the chromebook for example and it was not at all clear chrubuntu supports the very fast intel integrated display support....

Oh, my cell phone is just that, a phone, not a mobile tiny display with few short lines.

---

### Post by ventrical on 2013-05-14
> **cariboo907 said:**
> You're going to run into that, when you have the proposed repositories enabled, they are more or less being used to store packages, until all the dependencies have been built, and test have been passed.


Thank you very much. I assumed that.  I will continue then to experiment with Mir  concurrently with 13.04 and report  here until Saucy repos cough up some packets. :)

---

### Post by ventrical on 2013-05-14
The 'mir' executable is  broken , even in raring main (proposed disabled) .. so somthing bigger is running amuck, and I can't file a bug against it because it's being held back... err .. unless I file a psudeo-bug ! :)

---

### Post by ventrical on 2013-05-14
Sent an e-mail to developer , Kevin DuBois,  through launchpad.

best I can do for now unless I write my own server ! :)


zzz

---

### Post by serdotlinecho on 2013-05-14
Any chance to run Mir display server with tiling windows manager like i3, awesome or xmonad? :D

---

### Post by ventrical on 2013-05-15
It is obvious atm that tablets and phones are priority for Ubuntu and not desktop now while concerning Mir Server. I don't know .. perhaps on newer towers or exclusive hardware - which means  'other' hardware is not included and I guess it is my own fault for not seeing the writing on the wall that Mir desktop demo days were soon to come to an end for the interim. It would have been nice to have a heads up.

---

### Post by ventrical on 2013-05-15
> **ventrical said:**
> Sent an e-mail to developer , Kevin DuBois,  through launchpad.

best I can do for now unless I write my own server ! :)


zzz


So far , no reply from Kevin DuBois.

---

### Post by cariboo on 2013-05-15
@ventrical, check out Jono's video [here]("https://www.youtube.com/watch?v=E9AzRxsnfTE"). According to this post @ [OMG! Ubuntu]("http://www.omgubuntu.co.uk/2013/05/unity-8-gets-demoed-on-mir-looks-impressive-already"), we should be able to test Unity and Mir later in the dev cycle. It looks like we'll be getting Unity 7 by default on Saucy.

---

### Post by ventrical on 2013-05-16
@cariboo907

Thanks for the links.  I must admit, I still don't get it.  Am I to assume that those demos are on Tablet PCs? (It appeared that some others were on desktop PCs).  I guess my alternate question is;  is anybody else able to  download the 'mir'   file from the ppa without getting broken depends?

  Since the rollover to Saucy development, Mir all of a sudden becomes broken, even for raring. It is very perplexing at this stage of the game.

 I'll keep trying.

Edit:

 Btw ... that demo looked and performed  exactly like the Windows 8 Enterprise Edition which  works exceptionally well on towers and laptops.

 

:)

---

### Post by grahammechanical on 2013-05-16
Today at UDS UTC 14:00 there is a session called Delivering a Unity 8 Desktop in Ubuntu 13.10. From Planet Ubuntu I have found this

[http://kdubois.net/?p=1845](http://kdubois.net/?p=1845)

[http://unity.ubuntu.com/getinvolved/development/unitynext/](http://unity.ubuntu.com/getinvolved/development/unitynext/)

I tried to put Unity 8 on saucy but the repos are not there. Need to change the URL to raring. I tried again on an old install on Raring. It failed at the last hurdle of trying to run the people lens daemon and UnityNext shell. The Phone app came up. It is starting to look nice. Does not work as an app. It has got specimen data. As these installs had stuff from other PPAs I will try again with "pure" Raring and Saucy.

But I am getting confident that we will be seeing stuff in Saucy before we get the running the TIP or whatever name they decide to call the rolling development branch.

Regards.

---

### Post by ventrical on 2013-05-16
> **grahammechanical said:**
> @ventrical

I have not yet seen this video. It is a Ubuntu On Air discussion by the developers about Mir and the next Unity.

[http://www.youtube.com/UbuntuOnAir](http://www.youtube.com/UbuntuOnAir)

It is only now being posted to youtube. So, we need to give them so time to set things up.

Regards.

@grahammechanical

I watched 2 and 1/2 minutes of this and got totally lost. It looked like Phil Collins' little brother :)

[http://www.youtube.com/watch?v=Jnh7kW_XMY0](http://www.youtube.com/watch?v=Jnh7kW_XMY0)

---

### Post by grahammechanical on 2013-05-16
@ventrical

I know what you mean. Jono's Q&A is a free wheeling chat but sometimes we get nuggets of where things are going. I do struggle with listening at UDS but at least I can get on with some other stuff at the same time and process is open and there is nothing stopping us from trying to make a point. I think that there is a genuine attempt to get information out there.

Yesterday, I found out that Mark wanted the rolling release to be called raring. That tells me that Mark doesn't want any more interim releases. That he wanted 13.04 to going into continue development mode. And that TIP, ROLLING, NEXT are favourite names. And we will be offered the option to subscribe to our saucy repos URL  becoming a symlink that will naturally point to the repo URL of the next development branch.

I would like to suggest that the development rolling branch be called Ubuntu [FONT=arial]manãna. I have read that it means "not today."

Edit: Well the UDS session Desktop Unity Polish 13.10 was a flop. It finished after 30 minutes with nothing much said and nothing left to say. These guys might be clever at coding but they cannot communicate even among themselves. [/FONT]

---

### Post by ventrical on 2013-05-16
@grahammechanical

Thanks for all your help and information presented on this matter. A very intriguing read.

---

### Post by checoimg on 2013-06-09
> **grahammechanical said:**
> @ventrical

I would like to suggest that the development rolling branch be called Ubuntu [FONT=arial]manãna. I have read that it means "not today."

[/FONT]

[FONT=arial]manãna = tomorrow[/FONT]

---

### Post by checoimg on 2013-06-09
Before reading the whole thread I will ask : Which are the commands to run Mir ?

I followed the instructions here : [http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html](http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html)

---

### Post by ventrical on 2013-06-09
> **checoimg said:**
> Before reading the whole thread I will ask : Which are the commands to run Mir ?

I followed the instructions here : [http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html](http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html)


It appears the whole format has changed since I last tested the mir_demos. Read the whole thread. If you are using a desktop (non-touch) you will need the 'mir' executable in /usr/bin  to run the mir_demos. As it stands, the 'mir' exectuable will not install without breaking the libmirserver and vis a versa.

 I tried to talk to the devs about this but no answer.

---

### Post by checoimg on 2013-06-09
> **ventrical said:**
> It appears the whole format has changed since I last tested the mir_demos. Read the whole thread. If you are using a desktop (non-touch) you will need the 'mir' executable in /usr/bin  to run the mir_demos. As it stands, the 'mir' exectuable will not install without breaking the libmirserver and vis a versa.

 I tried to talk to the devs about this but no answer.

Too bad Mir is no there.

---

### Post by cariboo on 2013-06-09
I know that many of you are anxious to test what's coming, but it's still fairly early in the development cycle. When Unity8 and Mir become available for testing on the desktop, we will get ample notice.

---

### Post by ventrical on 2013-06-10
> **cariboo907 said:**
> I know that many of you are anxious to test what's coming, but it's still fairly early in the development cycle. When Unity8 and Mir become available for testing on the desktop, we will get ample notice.



Thanks for that notification.

Regards,
Ventrical

---

### Post by ventrical on 2013-06-11
Christopher Halse Rogers wrote to ventrical concerning "mir' executable:

> 
Ah, right. Yes.
  There is no longer a mir binary, as it was a bit confusing. It's now mir_demo_server (or mir_demo_server_shell).





---

### Post by EgoGratis on 2013-06-13
[http://blog.martin-graesslin.com/blog/2013/06/starting-a-full-kde-plasma-session-in-wayland/](http://blog.martin-graesslin.com/blog/2013/06/starting-a-full-kde-plasma-session-in-wayland/)

About Mir where is that demo session we are waiting for? We all know it is not yet finished and it will be not for some time but this is Ubuntu +1 and we want to test regardless on a daily basis...

---

### Post by cecilpierce on 2013-06-14
Must be TOP secret !

---

### Post by EgoGratis on 2013-06-14
Core Apps it looks like are proceeding nicely:

[http://www.iloveubuntu.net/ubuntu-touchs-gallery-app-and-media-player-app-landed-ubuntu-1310s-ubuntu-software-center](http://www.iloveubuntu.net/ubuntu-touchs-gallery-app-and-media-player-app-landed-ubuntu-1310s-ubuntu-software-center)

Unity + Mir it looks like a lot of effort it's being put in it ATM:

[http://bregmatter.wordpress.com/2013/06/14/ubuntu-desktop-convergence/](http://bregmatter.wordpress.com/2013/06/14/ubuntu-desktop-convergence/)

I do see the possibility to be able to sum it all up by the end of the year and do some serious testing. :) 

P.S. It will be interesting autumn/winter testing period this time by the looks of it and i guess no summer vacation for the devs this year! :)

---

### Post by EgoGratis on 2013-06-22
The game is on:

[http://www.phoronix.com/scan.php?page=news_item&px=MTM5Mzc](http://www.phoronix.com/scan.php?page=news_item&px=MTM5Mzc)

---

### Post by grahammechanical on 2013-06-22
Thanks for the link. I tried again with the core apps the other day. They install but do not load. I guess they need the SDK also installed. I found that to be the case last time I experimented with them. I think that the SDK brings in QML libraries that are not yet part of the standard saucy system.

I will also try that MIR PPA. It seems like progress.

Regards.

---

### Post by EgoGratis on 2013-06-22
> **grahammechanical said:**
> Thanks for the link. I tried again with the core apps the other day. They install but do not load. I guess they need the SDK also installed. I found that to be the case last time I experimented with them. I think that the SDK brings in QML libraries that are not yet part of the standard saucy system.

I will also try that MIR PPA. It seems like progress.

Regards.

Yes ATM i think this is correct.

---

### Post by ventrical on 2013-06-22
@graham

Do you mean this one here ?

**ppa:phablet-team/mir**

---

### Post by ventrical on 2013-06-22
> **grahammechanical said:**
> Thanks for the link. I tried again with the core apps the other day. They install but do not load. I guess they need the SDK also installed. I found that to be the case last time I experimented with them. I think that the SDK brings in QML libraries that are not yet part of the standard saucy system.

I will also try that MIR PPA. It seems like progress.

Regards.  

The Calendar and Calculator apps load and work great here.

---

### Post by EgoGratis on 2013-06-25
> **EgoGratis said:**
> The game is on:

[http://www.phoronix.com/scan.php?page=news_item&px=MTM5Mzc](http://www.phoronix.com/scan.php?page=news_item&px=MTM5Mzc)

I thought failed unity8 build (amd64 i386) 4 days ago would be fixed sooner and we would be able to test the PPA by now (i guess the fun is on ARM devices ATM)!

---

### Post by ventrical on 2013-06-25
> **EgoGratis said:**
> I thought failed unity8 build (amd64 i386) 4 days ago would be fixed sooner and we would be able to test the PPA by now (i guess the fun is on ARM devices ATM)!


 Go figure .. I hope they have lots of fun :)

---

### Post by cariboo on 2013-06-25
Now that there are Saucy builds of mir, I think this thread has outlived it's usefulness. Please refer to this [thread]("http://ubuntuforums.org/showthread.php?t=2157228") for more mir fun. Thread closed.

---

