---
title: "Running Warcraft III"
date: 2009-05-31
forum: Wine
---

### Post by BluePlum on 2009-05-31
Hello,

I know you must get allot of these threads, so I apologise, I have searched for the answer but being new to ubuntu I was over whelmed with confusion in other threads.

After I installed warcraft III, my problem persists with running the game. It is very slow, jumpy, and glitchy, I have disabled compiz, and to my understanding of the matter, I need to run warcraft III in opengl, but I do not know how to go about this.

Thank you in advance,

Andrew.

---

### Post by ruzkie on 2009-05-31
-opengl

---

### Post by BluePlum on 2009-05-31
Sorry I don't understand what you mean.

---

### Post by oldrocker99 on 2009-05-31
I believe he means something like

> wine warcraft3.exe -opengl

Try that, anyway.:D

:guitar:

---

### Post by BluePlum on 2009-06-01
Tried that , Error below.

```
andrew@Invisible-Assasin:~$ wine warcraft3.exe -opengl
wine: could not load L"C:\\windows\\system32\\warcraft3.exe": Module not found
```

---

### Post by hikaricore on 2009-06-01
Assuming you didn't install WC3 in your home directory... that would be why it's not working.

Your wine directory is located at:  /home/username/.wine
Inside that would be the drives mapped in winecfg.

So drive C would be: /home/username/.wine/drive_c/
And modern programs like warcraft III would likely be installed under program files: /home/username/.wine/drive_c/Program\ Files/
And depending on the actual directory you installed WCIII in you'd need to change to that directory like such:

cd /home/username/.wine/drive_c/Program\ Files/Warcraft3

and then run: wine warcraft3.exe -opengl

Again this all depends on where you installed it.

---

### Post by hikaricore on 2009-06-01
You're also going to make sure you have decent video hardware that supports OpenGL.

---

### Post by BluePlum on 2009-06-01
So how do I get it working? And My Video card can handle it,

Thanks Again.

---

### Post by nolliecrooked on 2009-06-01
what is your graphics card?

---

### Post by BluePlum on 2009-06-01
ATI Radeon 9000, Old but could run WC3 fine on windows.

---

### Post by nolliecrooked on 2009-06-01
> **BluePlum said:**
> ATI Radeon 9000, Old but could run WC3 fine on windows.

oh man, for like the 1000000000000000000 time, ATis Linux drivers are crap compared to the Windows ones. that chip is pretty low end anyway, and has to use old drivers.

if you have ATi;

**STAY. WITH. WINDOWS**

its much easier :)

---

### Post by BluePlum on 2009-06-01
Yes, but on 7.10 a fair while ago, I was running wc3 fine because I added the -opengl command to the line, but now when I try this I get an error so if someone could please help me in detail to over come this problem it'd be great.

Thanks.

---

### Post by ruzkie on 2009-06-01
in what dir are you when you type the wine command also what wine version are you using and how did you install wc3

---

### Post by del_diablo on 2009-06-01
Ubntu 9.04 + ATI older than Radeon 2000 = no 3D drivers
Lets just get that clear. For newer cards my experience is quite good, the drivers work quite well. Well the catalyst 9.3 was quite well as a driver too, but sadly it did not support 1.6 of Xorg(for the note that was the last one who supported older than Radeon 2000).
A note is that i did not need the openGL flag last time i played either, which i found quite good.
Another note: Remove the "Movie" folder, it cannot be ran............. yet
Another note, patch the game............

---

### Post by racerraul on 2009-06-02
you need to point wine to the directory where you have Warcraft installed.

For example...

wine .wine/drive_c/Program\ Files/Warcraft\ III/war3.exe -opengl

or if for example its in your Games folder within your home folder then....

wine ~/Games/Warcraft\ III/war3.exe -opengl

---

