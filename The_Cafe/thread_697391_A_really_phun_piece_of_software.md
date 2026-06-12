---
title: "A really phun piece of software"
date: 2008-02-15
forum: The Cafe
---

### Post by Garyu on 2008-02-15
A friend of my brothers did this piece of software that emulates physics. When my brother told me to check it out I was like, meh, I hate physics. But this piece of software actually looks like loads of phun! :D

[http://www.youtube.com/watch?v=0H5g9VS0ENM](http://www.youtube.com/watch?v=0H5g9VS0ENM)
The windows are wobbly, so it looks like he is running it in linux. There is some link to the software, but I never did anything else than look at the YouTube video. ^^

---

### Post by walkerk on 2008-02-15
That was pretty cool...

---

### Post by JurB on 2008-02-15
[Download link]("http://www.acc.umu.se/%7Eemilk/")

Can't wait to get home and play...
I sent an email to the developer regarding the license, let's hope it's GPL.

---

### Post by rowanparker on 2008-02-15
I tried it but recieved this error:
>  ERROR: This system doesn't support shaders. Please update your graphics driver and try again
I have rather an old video card and have no idea about the drivers (okay, I could do it but everything else works fine like compiz).
Anyway to add 'shaders' support to X using the standard ati driver.

---

### Post by luctor on 2008-02-15
So cool !!

---

### Post by wieman01 on 2008-02-15
Oh my gosh, this is so much fun. Hilarious. I have just wasted an hour playing it!

---

### Post by JurB on 2008-02-15
Me wanna play, i have to wait 5 hours before i can :(
I know what i'm gonna do this WE ;)

---

### Post by mr.propre on 2008-02-15
I played it on my windows vista machien, and its a fun little game. :KS

---

### Post by angry_johnnie on 2008-02-15
so how'd you install it?  i downloaded it, and tried running the executable, but all i get is a black window, which stays open for about a second or two.  the readme file didn't shed any light.  am i missing something?

---

### Post by hyper_ch on 2008-02-15
this is cool :)

---

### Post by Zlatan on 2008-02-15
fabulous:)

---

### Post by icechen1 on 2008-02-15
> **angry_johnnie said:**
> so how'd you install it?  i downloaded it, and tried running the executable, but all i get is a black window, which stays open for about a second or two.  the readme file didn't shed any light.  am i missing something?

some here :( says a segmentation fault in the terminal.)

---

### Post by koleoptero on 2008-02-15
Could someone post some info on how you made this to run? :confused:

---

### Post by forrestcupp on 2008-02-15
Pretty awesome.  I'm going to try that out.  I didn't know 2D could be that cool.

---

### Post by conehead77 on 2008-02-15
i made it executable with
chmod 777 phun_beta_2_3_linux32
, then just run it with 
./phun_beta_2_3_linux32

hope it works for you aswell :)

---

### Post by lode on 2008-02-15
> **conehead77 said:**
> i made it executable with
chmod 777 phun_beta_2_3_linux32
, then just run it with 
./phun_beta_2_3_linux32

hope it works for you aswell :)


My terminal says: 

```
Parsing autoexec.cfg...
Creating window...
Segmentation fault (core dumped)
```

Wouldn't have the slightest idea what that means.

It looks really fun (the YouTube video, that is), though.

---

### Post by Havoc on 2008-02-15
It plays on my Feisty machine.

---

### Post by JurB on 2008-02-15
Maybe you should post your problem [here.]("http://www.gamedev.net/community/forums/topic.asp?topic_id=482775")

---

### Post by icechen1 on 2008-02-15
It says a segmentation fault probably because my computer dosen't have shader.oh well...

---

### Post by erginemr on 2008-02-15
> **icechen1 said:**
> It says a segmentation fault probably because my computer dosen't have shader.oh well...

What is your graphics card?

---

### Post by icechen1 on 2008-02-15
> **erginemr said:**
> What is your graphics card?
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
 here it is

---

### Post by erginemr on 2008-02-15
As far as I know, if:
```
glxinfo | grep GL_ARB_shader_objects
```
yields nothing, then it means you graphics card (or driver) does not support pixel shading.

---

### Post by icechen1 on 2008-02-15
> **erginemr said:**
> As far as I know, if:
```
glxinfo | grep GL_ARB_shader_objects
```
yields nothing, then it means you graphics card (or driver) does not support pixel shading.

Says nothing but [http://www.intel.com/support/graphics/sb/cs-014257.htm]("http://www.intel.com/support/graphics/sb/cs-014257.htm")
says it is supported...

---

### Post by meho_r on 2008-02-15
Problem with shader here too. Ati Radeon X1650 Pro and Ubuntu Restricted Graphic Card Driver, not one from Ati. Do I have to install Ati's driver to get shader support?

---

### Post by erginemr on 2008-02-15
> **meho_r said:**
> Problem with shader here too. Ati Radeon X1650 Pro and Ubuntu Restricted Graphic Card Driver, not one from Ati. Do I have to install Ati's driver to get shader support?

You should check your xorg.conf file:
```
less /etc/X11/xorg.conf
```
Look for the section:
```
Section "Device"
    Identifier     "nVidia Corporation NV17 [GeForce4 MX 440]"
    Driver         **[COLOR="Blue"]"nvidia"[/COLOR]**
    # Option       "MetaModes" "1024x768"
EndSection
```
If your driver says **[COLOR="Blue"]"ati"[/COLOR]** then you are using the open source version. On the other hand, if it says **[COLOR="Blue"]"fglrx"[/COLOR]** then you are already using the binary 3-D version.

---

### Post by erginemr on 2008-02-15
> **icechen1 said:**
> Says nothing but [http://www.intel.com/support/graphics/sb/cs-014257.htm]("http://www.intel.com/support/graphics/sb/cs-014257.htm")
says it is supported...

Are you able to use Compiz (desktop effects)?

And what is the output of "glxinfo | grep direct"?

---

### Post by icechen1 on 2008-02-15
> **erginemr said:**
> Are you able to use Compiz (desktop effects)?

And what is the output of "glxinfo | grep direct"?

I am using Compiz right now.
The driver is ''intel''
output is direct rendering:Yes

---

### Post by JurB on 2008-02-16
Did you check the necessary libraries as instructed in the README? (boost_filesystem, SDL, SDL_image and GLEW).

Weird, all i have to do  is make it  executable  and double-click to run.

Great phun btw!

---

### Post by meho_r on 2008-02-16
> **erginemr said:**
> You should check your xorg.conf file:
```
less /etc/X11/xorg.conf
```
Look for the section:
```
Section "Device"
    Identifier     "nVidia Corporation NV17 [GeForce4 MX 440]"
    Driver         **[COLOR="Blue"]"nvidia"[/COLOR]**
    # Option       "MetaModes" "1024x768"
EndSection
```
If your driver says **[COLOR="Blue"]"ati"[/COLOR]** then you are using the open source version. On the other hand, if it says **[COLOR="Blue"]"fglrx"[/COLOR]** then you are already using the binary 3-D version.
Yes, it is fglrx. Generally, 3D works with other apps. But Phun still asks for "shaders". However, I tried it on Win and it is really cool :)

---

### Post by meho_r on 2008-02-16
Sorry, double post :(

---

### Post by pythonusr on 2008-02-17
Bump here... I get the same segmentation fault. My card doesn't support pixel shading, but I added "App.shaders=false;" to autoexec.cfg and it still doesn't run.

Any help?

---

### Post by icechen1 on 2008-02-17
> **pythonusr said:**
> Bump here... I get the same segmentation fault. My card doesn't support pixel shading, but I added "App.shaders=false;" to autoexec.cfg and it still doesn't run.

Any help?

The newest version 2.51 beta works now by uncommenting that!

---

### Post by forrestcupp on 2008-02-19
I wish I could have two mice.  Sometimes it's hard to manipulate things one-handed.

---

### Post by gletob on 2008-02-19
has anyone tried turning of desktop effect in the appearance menu 
that fixed it for me

---

### Post by JordanII on 2008-02-19
```
jordan@jordan-desktop:~/Desktop$ cd Phun; ./phun;
Parsing autoexec.cfg...
Creating window...
!! ERROR: Exception caught in main: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
!! ERROR: Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
```

That's what I get. :( Could someone please help? I have integrated intel graphics.

---

### Post by Co.Sinecure on 2008-02-21
> **JordanII said:**
> ```
jordan@jordan-desktop:~/Desktop$ cd Phun; ./phun;
Parsing autoexec.cfg...
Creating window...
!! ERROR: Exception caught in main: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
!! ERROR: Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
```

That's what I get. :( Could someone please help? I have integrated intel graphics.

I get this also.. Tried pointing LD_LIBRARY_PATH to the phun directory as suggested, tried setting 'Resources.shaders = false;' in autoexec.cfg, made sure I had a whole bunch of SDL libs installed (when running without setting LD_LIBRARY_PATH)..

Any ideas?

---

### Post by bruce89 on 2008-02-21
Interesting.

```

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb743f720 (LWP 16242)]
0x00000000 in ?? ()
(gdb) bt
#0  0x00000000 in ?? ()
#1  0x08266846 in rendering::Shader::Shader ()
#2  0x0826fdae in LoadFromFiles ()
#3  0x08270458 in boost::detail::function::function_obj_invoker0<boost::_bi::bind_t<rendering::Shader*, rendering::Shader* (*)(std::string), boost::_bi::list1<boost::_bi::value<std::string> > >, rendering::Shader*>::invoke ()
#4  0x08270cc0 in boost::function0<rendering::Shader*, std::allocator<void> >::operator() ()
#5  0x0827253b in util::Mentor<rendering::Shader>::Load ()
#6  0x081d3ca2 in core::ResourceManager::LoadType ()
#7  0x081d478e in core::ResourceManager::LoadAll ()
#8  0x081e1a25 in core::Subsystem::CreateWindow ()
#9  0x081d12db in main ()

```

---

### Post by schmolch on 2008-02-21
Im getting a segfault as well.
32bit Version on 32bit Ubuntu on a Thinkpad with Intel integrated graphics with working 3D.

I was really waiting for a program like this, hopefully it will work soon.

---

### Post by schmolch on 2008-02-22
On my Desktop with the same 32bit Ubuntu but nvidia cards it works, so i guess its a video-card issue.

---

