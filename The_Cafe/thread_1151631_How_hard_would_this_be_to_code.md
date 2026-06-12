---
title: "How hard would this be to code?"
date: 2009-05-07
forum: The Cafe
---

### Post by toejamfootball on 2009-05-07
I was thinking about having a go at writing an app.

I have in mind a random scale generator. So I would just click a button, or something on the keyboard and instructions of which scale to play would come on the screen.

It would only need to tell me in text form what to play for eg. Play G Minor, or Play Ab Dorian..... things like that.

I'm just wondering how hard this would be, do you think this is something a beginner could do?

:)

---

### Post by fatality_uk on 2009-05-07
I know squat about music, however, seems very easy to code though.
A few arrays, one for instructions, one for scales/keys, etc, random number generator with time as a seed and bobs your uncle!!

This would be a good beginner project. Use something like GAMBAS(VB), MONO.

---

### Post by directhex on 2009-05-07
> **fatality_uk said:**
> I know squat about music, however, seems very easy to code though.
A few arrays, one for instructions, one for scales/keys, etc, random number generator with time as a seed and bobs your uncle!!

This would be a good beginner project. Use something like GAMBAS(VB), MONO.

Some languages make it easier to work with audio (including generated audio) than others. Mono's probably not your top pick here.

---

### Post by many_boomers on 2009-05-07
Easy, but not easy enough for me to stop looking at pr0n and try it. Maybe two or three functions, and knowing what headers/libraries to include (sorry, i don't). Just out of curiosity, what language are we talking about?

---

### Post by fatality_uk on 2009-05-07
> **directhex said:**
> Some languages make it easier to work with audio (including generated audio) than others. Mono's probably not your top pick here.

> It would only need to tell me in text form what to play for eg. Play G Minor, or Play Ab Dorian..... things like that.

Hence the GAMBAS/MONO option. No need to code for MIDI, or MP3 output. Unless the OP had some hidden meaning in it!!! But then again, I usually just read what people write and respond to that!

---

### Post by toejamfootball on 2009-05-07
> **fatality_uk said:**
> I know squat about music, however, seems very easy to code though.
A few arrays, one for instructions, one for scales/keys, etc, random number generator with time as a seed and bobs your uncle!!

This would be a good beginner project. Use something like GAMBAS(VB), MONO.

Thanks mate. I will look into those. Gotta find me some tutorials too, as I know absolutely nothing about this.

> **directhex said:**
> Some languages make it easier to work with audio (including generated audio) than others. Mono's probably not your top pick here.

Just need it to display Text, no audio.

> **many_boomers said:**
> Easy, but not easy enough for me to stop looking at pr0n and try it. Maybe two or three functions, and knowing what headers/libraries to include (sorry, i don't). Just out of curiosity, what language are we talking about?

By language do you mean certain code or something? (runs off to find tutorials)

EDIT: So I am Downloading GAMBAS as I type, and also reading the how to from their website......

---

### Post by directhex on 2009-05-07
Looks like I was adding requirements in my head. This would be pretty easy, I think. For pure text output you're really only talking about a random number generator with a lookup table, which is a 3 minute job.

For example, here's a C# version:

```
using System;

public class notey
{
	public static void Main( )
	{
		string[,] Chords = 
		{{"C major", "The plinky strings"},
		 {"A minor", "Don't bother, it's a depressing chord"},
		 {"E minor", "Go fly a kite instead"}};
		int NumberOfChords = Chords.Length / 2;
		Console.WriteLine( "{0} chords in database", NumberOfChords );
		Random RandomNumberObject = new Random( DateTime.Now.Millisecond );
		int SelectedNumber = RandomNumberObject.Next( NumberOfChords );
		Console.WriteLine( "Selected number {0}", SelectedNumber + 1 );
		Console.WriteLine( "*** PLAY {0} ***", Chords[SelectedNumber,0] );
		Console.WriteLine( "To plsy this chord, play: {0}", Chords[SelectedNumber,1] );
	}
}
```

Here's what the code above does:
```
jms@osc-bigmac:/tmp$ mono notey.exe 
3 chords in database
Selected number 3
*** PLAY E minor ***
To plsy this chord, play: Go fly a kite instead
jms@osc-bigmac:/tmp$ mono notey.exe 
3 chords in database
Selected number 3
*** PLAY E minor ***
To plsy this chord, play: Go fly a kite instead
jms@osc-bigmac:/tmp$ mono notey.exe 
3 chords in database
Selected number 1
*** PLAY C major ***
To plsy this chord, play: The plinky strings
jms@osc-bigmac:/tmp$ mono notey.exe 
3 chords in database
Selected number 2
*** PLAY A minor ***
To plsy this chord, play: Don't bother, it's a depressing chord
```

---

### Post by 3rdalbum on 2009-05-07
Occam's Razor applies to programming too. You don't need to break out MonoDevelop or Gambas to write an app like this. You don't need weighty visual IDEs, and you don't need languages that take ten lines of code just to write to a file.

I'd write the program in Javascript. A couple of arrays, a random number generator, a button triggering the randomise script, and do all your formatting in HTML (or, of course, use Seamonkey Composer to create the layout).

---

### Post by toejamfootball on 2009-05-07
> **directhex said:**
> Looks like I was adding requirements in my head. This would be pretty easy, I think. For pure text output you're really only talking about a random number generator with a lookup table, which is a 3 minute job.

For example, here's a C# version:

```
using System;

public class notey
{
	public static void Main( )
	{
		string[,] Chords = 
		{{"C major", "The plinky strings"},
		 {"A minor", "Don't bother, it's a depressing chord"},
		 {"E minor", "Go fly a kite instead"}};
		int NumberOfChords = Chords.Length / 2;
		Console.WriteLine( "{0} chords in database", NumberOfChords );
		Random RandomNumberObject = new Random( DateTime.Now.Millisecond );
		int SelectedNumber = RandomNumberObject.Next( NumberOfChords );
		Console.WriteLine( "Selected number {0}", SelectedNumber + 1 );
		Console.WriteLine( "*** PLAY {0} ***", Chords[SelectedNumber,0] );
		Console.WriteLine( "To plsy this chord, play: {0}", Chords[SelectedNumber,1] );
	}
}
```

Here's what the code above does:
```
jms@osc-bigmac:/tmp$ mono notey.exe 
3 chords in database
Selected number 3
*** PLAY E minor ***
To plsy this chord, play: Go fly a kite instead
jms@osc-bigmac:/tmp$ mono notey.exe 
3 chords in database
Selected number 3
*** PLAY E minor ***
To plsy this chord, play: Go fly a kite instead
jms@osc-bigmac:/tmp$ mono notey.exe 
3 chords in database
Selected number 1
*** PLAY C major ***
To plsy this chord, play: The plinky strings
jms@osc-bigmac:/tmp$ mono notey.exe 
3 chords in database
Selected number 2
*** PLAY A minor ***
To plsy this chord, play: Don't bother, it's a depressing chord
```
Cool. Sort of, does anyone know of a good tutorial for this sort of thing. I don't understand any of it.... :)

I would love to get into it, and find some sort of tutorial that will allow me to make this app myself....

---

### Post by toejamfootball on 2009-05-07
> **toejamfootball said:**
> Cool. Sort of, does anyone know of a good tutorial for this sort of thing. I don't understand any of it.... :)

I would love to get into it, and find some sort of tutorial that will allow me to make this app myself....
OK, I have aboslutley no idea where to even start. If someone could point me in the direction of tutorials that would be great. I had no luck finding any.......

---

### Post by kirsis on 2009-05-07
1. Install python
2. You'll need lists and, likely, knowledge of what '%' does (hint: 7 % 6 = 1 but 2 % 3 = 2)

3. I threw a little script together that can print out scales, given the key and scale template (intervals in the scale). Works a like this:

major_scale = [2, 2, 1, 2, 2, 2]
blues_scale = [3, 2, 1, 1, 3]
print (get_scale("C", major_scale))
>>> ['C', 'D', 'E', 'F', 'G', 'A', 'B']
print (get_scale("C", blues_scale))
>>> ['C', 'Eb', 'F', 'Gb', 'G', 'Bb']

Here's a few tips:

[LIST]
[*]You'll need a function that can return a note given its index (0 => A, 1 => A#, 2 => B, 12 => A again)
[*]You'll need a function that can do the reverse - get the index of a key (A => 0, 12 => A, 13 => A#)
[*]When you have these functions, it should be easy to write a get_scale function that assembles a scale like this: key note + all the notes at intervals specified in the scale template
[*]I used only #s and no flats when constructing the scale. Then when a scale has been assembled, I used a sanitizer function, which, if needed, turned the sharps into flats.
[/LIST]

If you're interested, I can show you the code.


edit: P.S. While everything can be solved with lookup tables (as proven by thedailywtf.com), there's no need for them in solving this problem

edit2: actually, scratch the first 2 points. Just put the notes in a list and use notes[index] to get a note by index and notes.index(note) to get a particular note's index. I started out with a different algorithm in mind (sanitizing # and b on the fly, rather than at the end) and just realized I have it a bit too convoluted, lol

---

### Post by Bölvaður on 2009-05-07
you will need to get some basics down in.. well just any programming language, most of them will do.


You can make 2 programs (see the reason why below)

1. you'd type the name of the program and the scale you want and also a file to write the riff to.

$ randommelody Cminor outputfile.txt

and it will just make a simple txt file. I guess making midi file wouldn't be much harder.

input: scale , a string variable telling which scale the random function will use
         fileName, a string variable
output : riff, variable, written into the fileName document.

then you can do what ever you want with the info you get. you can have the output file as midi and play it in totem, you can have it a text file and have another program to display it as guitar tabs.....

---

### Post by Luggy on 2009-05-07
Well from the sound of it the application shouldn't be too hard to code, but the devil is always in the details.

The more basic the application, the easier it will be to code.
From the way you described it, I don't really know what you want the output to be.

If you are keen to write this yourself the first thing you should do is pick a language, learn it, then start working on your applicatoin.

Sorry, but you gotta crawl before you can run.

I'd recommend Python as it is easy to learn and documentation for it is very simple ([http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)).

---

