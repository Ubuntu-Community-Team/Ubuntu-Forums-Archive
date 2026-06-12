---
title: "Black on White Console?"
date: 2010-06-27
forum: The Cafe
---

### Post by Penguin Guy on 2010-06-27
Computers have always had a white-on-black console, but why? Is it some BIOS thing, or is it to do with the kernel? Personally, I'd prefer a black-on-white console, but I've never even seen one before. What do you think?

Is there any way to change the console's colors? (I mean the *actual* console)

---

### Post by CharlesA on 2010-06-27
You can change the color of the terminal from within the OS. Outside the OS, it normally just defaults to white on black for whatever reason.

---

### Post by Simian Man on 2010-06-27
On older CRT monitors, it took more energy to display white pixels than black ones.  Perhaps that has something to do with it.

---

### Post by dragos240 on 2010-06-27
I prefer green on black. Nice old hacker look.

---

### Post by TheNessus on 2010-06-27
you mentioned BIOS. I think I'll change my black on white, to white on blue, like BIOS. :)

---

### Post by betrunkenaffe on 2010-06-27
> **dragos240 said:**
> I prefer green on black. Nice old hacker look.

Remember using the dumb terminals at the University, green on black.. :)

---

### Post by skaarr on 2010-06-27
Yellow on black for me.

---

### Post by TheLions on 2010-06-27
black text on white surface burns my eys while coding in small hours...

Lucky there is compiz negative plugin, which instantly change colors.

---

### Post by Penguin Guy on 2010-06-27
Okay, so a lot of you prefer black background color, but for those that don't, is there any way to change it? (I mean the *actual* console, not an Xorg-based terminal)

---

### Post by chriswyatt on 2010-06-27
I like green on black not just for the retro look but it's a good readable colour scheme as well.  Not a fan of white and black, I prefer grey on black, white on black is kind of harsh.

---

### Post by devondashla on 2010-06-27
> **Penguin Guy said:**
> Okay, so a lot of you prefer black background color, but for those that don't, is there any way to change it? (I mean the *actual* console, not an Xorg-based one)

Even if there is a way to change it, I wouldn't be surprised if it's more trouble than it's worth.

---

### Post by NCLI on 2010-06-27
> **Simian Man said:**
> On older CRT monitors, it took more energy to display white pixels than black ones.  Perhaps that has something to do with it.

And when we make the switch to OLED, that will once again be the case.

---

### Post by koenn on 2010-06-27
> **Simian Man said:**
> On older CRT monitors, it took more energy to display white pixels than black ones.  Perhaps that has something to do with it.

A CRT works by 'shooting' electrons towards a phosphorous layer, which lights up where the electrons hit. You basically 'paint' characters on the screen by manipulating the electron stream with electromagnets. Some screens used phosphor that glows green or orange. 

For a 'black on white' effect you'd have to illuminate a larger area, probably needing a bit more energy. It's probably also a bit more complex regarding the steering of the beam.

That said, I remember Toshiba laptops in the 80s or so where you could switch to 'black on white'. Don't quite remember how, a BIOS setting maybe.

---

### Post by Stancel on 2010-06-27
I prefer green on black. It just looks cool.:guitar:

---

### Post by prodigy_ on 2010-06-27
White on black of course. Or white on dark red for root shell to not forget to use it with caution.

---

### Post by lisati on 2010-06-27
The monitor for a machine I used to have used brown (sepia?) on black as its default. Before I had Windows, I sometimes used bright white on blue for some things in ASM programs for a CGA monitor on another machine.

---

### Post by lostinxlation on 2010-06-27
> **Penguin Guy said:**
> Okay, so a lot of you prefer black background color, but for those that don't, is there any way to change it? (I mean the *actual* console, not an Xorg-based terminal)
Have you tried escape sequence ?
 
I hate green on black. It just reminds me of JCL which was a real mess.
 
EDIT: Oh wait, you want a white background. Escape sequence doesn't work.

---

### Post by koenn on 2010-06-27
> **Penguin Guy said:**
> 
Is there any way to change the console's colors? (I mean the *actual* console)

yes, apparently.
You can send commands to the console to configure it. Some of those change the colors.

```

echo -e "\033[37m"

```
will give you something that resembles that old school hakerish green on black.

you could put this in a profile or a bashrc, or an init/upstart script, eg the one that configures the console.

You can do black text on white with 
```

echo -e "\033[7m"

```
 but it only paints the background in cells where there are characters.

Here's some background:[http://www.developer.com/open/article.php/631241/Linux-Console-Colors--Other-Tricks.htm](http://www.developer.com/open/article.php/631241/Linux-Console-Colors--Other-Tricks.htm)

the numbers between [ and m are the actual console commands, you can find them here : [http://linux.die.net/man/4/console_codes](http://linux.die.net/man/4/console_codes) -> scroll to ECMA-48 Set Graphics Rendition

For a complete white screen with black characters, you'd need to illuminate the entire screen in stead of only the cell where a character is displayed, while still keeping track of where the next character needs to be. That is apparently a bit harder than just changing foreground/background of 1 cell.
You probably need to work with framebuffer to do that.
[https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer)

---

### Post by K.Mandla on 2010-06-27
```
setterm -foreground green -background black -bold
```
Now you just need a way-cool 80's-ish hacker console font. ... :twisted:

---

### Post by Penguin Guy on 2010-07-06
[This article]("http://blog.nix.is/theming-the-linux-console") looks promising, it's got some C and Perl code for changing the 'palette', but I can't make sense of either of them - anyone here familiar with those languages?

---

### Post by Bachstelze on 2010-07-06
Neither. #BBBBBBBB on black.

---

### Post by koenn on 2010-07-06
> This article looks promising, it's got some C and Perl code for changing the 'palette', but I can't make sense of either of them - anyone here familiar with those languages?

looks like it's the same console escape code technique lostinxlation and I mentioned before. The additional code is to change to color palette, i.e. the set of colors  you get to choose from. AFAICT, anyway.

---

### Post by v1ad on 2010-07-06
> **TheNessus said:**
> you mentioned BIOS. I think I'll change my black on white, to white on blue, like BIOS. :)

o that reminded me of microsofts bsod.

---

### Post by Crunchy the Headcrab on 2010-07-06
> **v1ad said:**
> o that reminded me of microsofts bsod.
Me too. *Cringe*

---

### Post by koenn on 2010-07-06
> **v1ad said:**
> o that reminded me of microsofts bsod.
in the MS DOS era, long before BSOD, Microsoft used white on blue for text editots a.o., because studies had showed that it's a very good color scheme : easy to read while  easy on the eyes

---

### Post by Shining Arcanine on 2010-07-06
> **koenn said:**
> A CRT works by 'shooting' electrons towards a phosphorous layer, which lights up where the electrons hit. You basically 'paint' characters on the screen by manipulating the electron stream with electromagnets. Some screens used phosphor that glows green or orange. 

For a 'black on white' effect you'd have to illuminate a larger area, probably needing a bit more energy. It's probably also a bit more complex regarding the steering of the beam.

That said, I remember Toshiba laptops in the 80s or so where you could switch to 'black on white'. Don't quite remember how, a BIOS setting maybe.

I believe that the beam moves the same way regardless of the image on the screen. It needs to be able to display the full range of possible images and display them at a predefined refresh rate, so cutting corners by taking short cuts in special cases is something that cannot be done. Deviating from the "hit all pixels on the screen" pattern in a manner that optimizes the movement of the beam ruins the concept of a refresh rate and figuring out the exact path is a NP-Complete problem that cannot be solved in the time necessary for the CRT to function. It also introduces other issues, like display lag, because then the monitor cannot be drawing pixels as they are transmitted from your video card.

---

### Post by samalex on 2010-07-06
> **dragos240 said:**
> I prefer green on black. Nice old hacker look.

Ditto on this... that or amber on black.  Dyslexia makes it hard for me to read black or any colored text on white.

Sam

---

### Post by koenn on 2010-07-06
> **Shining Arcanine said:**
> I believe that the beam moves the same way regardless of the image on the screen. It needs to be able to display the full range of possible images and display them at a predefined refresh rate, so cutting corners by taking short cuts in special cases is something that cannot be done. Deviating from the "hit all pixels on the screen" pattern in a manner that optimizes the movement of the beam ruins the concept of a refresh rate and figuring out the exact path is a NP-Complete problem that cannot be solved in the time necessary for the CRT to function. It also introduces other issues, like display lag, because then the monitor cannot be drawing pixels as they are transmitted from your video card.

OK, I can somewhat follow that when I think about a bitmapped screen.

However, the console driver works with a grid of 80x25 cells (or something close to that), and a character fills that cell. 
So maybe it's more an issue of the software that does not paint backgrounds of whatever color in cells that do not have a character in it.

In any case, my understanding of this is probably rather simplistic. But in that case, I'd really like to hear an explanation of why 'inversing' the console (black on white bg) still leaves most of the screen black.

Or in other words, if that beam hits all pixels regardless, why can't one make it illuminate all pixels except the character shapes ?

---

### Post by Brunellus on 2010-07-06
I had to do a bit of looking, but I did do a bit of console customization on one ubuntu install--see this ancient blog post:

[http://ouij.livejournal.com/207594.html](http://ouij.livejournal.com/207594.html)

Although after looking around, it appears that none of that information is relevant to more recent versions of ubuntu.

---

### Post by WinterRain on 2010-07-06
I like neither. Green on black for me.

---

### Post by yester64 on 2010-07-06
First i thought you meant a (game) console.
There was this saying. If you want to play adventure on a pc, use DOS and be happy.

I think (secondly) that it is because of the PC heritage. To this day you still see all these unnecessary information popping up at boot. 
This should be hidden and not shown. Just a part of a PC.

---

### Post by Brunellus on 2010-07-06
> **yester64 said:**
> First i thought you meant a (game) console.
There was this saying. If you want to play adventure on a pc, use DOS and be happy.

I think (secondly) that it is because of the PC heritage. To this day you still see all these unnecessary information popping up at boot. 
This should be hidden and not shown. Just a part of a PC.
as a personal matter, I like seeing the boot messages, because I can figure out what's gone WRONG when something goes wrong.  With "slick" bootsplashes that cover all those ugly internals, you're left wondering why your shiny wondertoy won't boot--and have no real way of starting to understand the problem.

---

### Post by yester64 on 2010-07-06
> **Brunellus said:**
> as a personal matter, I like seeing the boot messages, because I can figure out what's gone WRONG when something goes wrong.  With "slick" bootsplashes that cover all those ugly internals, you're left wondering why your shiny wondertoy won't boot--and have no real way of starting to understand the problem.

Mm.. i take that.
But to be honest, there are not so many instances when something really goes wrong at boot.
I rarely had any issues in that regard since i run pc's. But like i said, i take it. Just my humble opinion.

---

