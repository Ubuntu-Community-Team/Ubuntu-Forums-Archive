---
title: "Alternative to FontForge?"
date: 2008-09-16
forum: Ubuntu Studio
---

### Post by Mahinva on 2008-09-16
I have downloaded and taken a look at FontForge, however I was wondering what alternatives may exist. I was not able to find much by searching through Synaptic, and searching online has only turned up applications that seem to be PC compatible. Perhaps there is a PC application that runs well on Wine that I haven't found?

For my purposes, I have a pixel font, and therefore would feel more comfortable with a "paintbrush" approach, with pixel radius set to 1x. In theory, this would make my modifying go very quick. I do not feel too comfortable working with FontForge, nor do I want to spend too much time modifying as I've no desire to become a typographer.

Any feedback or advice is appreciated. :)

---

### Post by Mahinva on 2008-09-18
Hope-filled bump!

---

### Post by Mahinva on 2008-09-20
I hate to bump again, but I've still found nothing.

---

### Post by paulmerchant on 2008-09-20
I found a bitmap font editor here:

[http://www.math.nmsu.edu/~mleisher/Software/gbdfed/](http://www.math.nmsu.edu/~mleisher/Software/gbdfed/)

Maybe it will help you.

---

### Post by Mahinva on 2008-09-20
Thank you very much :D

As I'm still learning my way around Ubuntu, I am trying to figure out how to compile this application (don't think I've had to yet). If/when I can figure out how to compile, I will give this program a shot.

---

### Post by paulmerchant on 2008-09-20
Compiling:

1. Download the source files and unpack them somewhere.

2. Read the README file. (This project doesn't appear to have a very newbie friendly README, but it should still give you some good information about the application and how to compile and use it.)

3. Open the terminal and navigate to the folder where you unpacked the source files. Type "./configure" and press Enter.

4. The configure script you just ran will show you if you have any missing dependencies. Sudo apt-get the dependencies. (Make sure you are grabbing source packages, when required. You might need to enable some of the source repositories. You can always use Synaptic to search or browse for the needed packages or enable source repositories.) Your configure script will need to complete showing that all required dependencies are present.

5. Now, back in the terminal (inside the folder with the source files) type "make" and press Enter.

6. Once everything has compiled, type "sudo make install". Sometimes you have to follow other steps. (In this case, you should be able to run the program by typing its name in the terminal and the files will end up under /usr/local.)

Compiling usually isn't too hard (unless it doesn't work). Let us know if you have any troubles.

---

### Post by Mahinva on 2008-09-21
Thank you for the instructions - although I have installed many programs since initially setting up Ubuntu, all of them have allowed me to do so without going through the terminal.

This worked wonderfully :) I was also able to create a desktop launcher for the program and then added it to my menu (to keep desktop clean). Now I just hope this application fits my needs! :)

---

