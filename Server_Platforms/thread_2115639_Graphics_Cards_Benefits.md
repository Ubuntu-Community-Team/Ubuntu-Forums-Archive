---
title: "Graphics Cards Benefits?"
date: 2013-02-13
forum: Server Platforms
---

### Post by SilverOrange on 2013-02-13
I have a server I installed ubuntu server 12.10, and I had a question. I currently have a AMD Radeon 6850 in it, does it provide any benefit at all? I don't have a desktop of any sort installed, it is all command line, so it is not like it will help the graphics. I am going to be running an apache web server off of it, and a java application (Minecraft). I will be doing other random stuff with it as well, I am in college for computer networking so I decided to get a jump start on linux before I got to that class. 

If it provides a benefit, do I have to install the drivers for it?

I have to say, once I got familiar with the basic commands, I fell in love with it. So much faster and simpler than Windows, no GUI based applications. 

Two more questions, kind of way off topic. I am still pretty new to linux, how would I start multiple processes and switch between them on the server? I know the screen command, but I can't seem to get it to work with the java application. Any body have a good guide for using it?
Last question, when I log into my server via SSH, is it possible for me to see the java application with that SSH session? So,  say the application is outputting something to the screen, and I am on my phone with SSH app and want to see what it is outputting and issue a command to it, how would I do that?


Thank you all for reading this, and helping if you can!

---

### Post by deadflowr on 2013-02-13
If you are running a server without a desktop environment or window manager, or even xserver, then installing the drivers for a graphic card is pointless.

---

### Post by d4m1r on 2013-02-13
It wouldn't hurt to install the proper drivers for it but I personally wouldn't bother putting in the effort to do so or using up the HDD space.

---

### Post by spynappels on 2013-02-14
You can background any process by adding & after the command to run it. This means the process keeps running in the background, and even closing the SSH session will not kill it. For example:

```
#:/path/to/long-running/executable
```

will run the executable (e.g. Minecraft Java process) but would kill it as soon as you logged out of the SSH session.

```
#:/path/to/long-running/executable &
```

wouldn't.

For more info on reconnecting to jobs running in the background:

```
man jobs
man fg
man bg
```

And no, I wouldn't worry about doing anything with the graphics card, most servers run completely headless with not even a monitor attached, and that's the way it was designed.

---

