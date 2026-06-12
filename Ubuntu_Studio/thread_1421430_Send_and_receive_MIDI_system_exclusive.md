---
title: "Send and receive MIDI system exclusive?"
date: 2010-03-04
forum: Ubuntu Studio
---

### Post by mango42 on 2010-03-04
I was hoping to use **Qtractor** to send and receive MIDI system exclusive bulk dumps etc to my hardware synths but the Sysex window only seems to want to import already stored files. I tried just setting a track to record sysex but nothing appeared to show up, whereas there's no problem recording MIDI notes and controllers.

Then I tried **amidi**

```
amidi -p=hw:1,0,5 -r=/home/xxxx/Music/HardwareConfig/OBxGrant.syx
```

but only got this error (permissions? Tried also with **sudo**)

"cannot create =/home/xxxx/Music/HardwareConfig/OBxGrant.syx: No such file or directory"

Anyone have experience with this issue - a search on this forum seemed to draw a blank? And yes, all synth parameters are setup correctly (ie: they work fine in those *other* OS's)

---

### Post by babarosa on 2010-03-04
Hi mango42,

the syntax of your commands is not correct, you need blanks between some arguments (-p xy and -r xy) and the path ist not correct ("=" is not the proper path information, it is for example ./ or ~/)!
Just copy your xy.syx file to your home directory, make dir in the terminal and copy and paste it into the command line (you can save this in .batch-history).


Find here examples for correct commands: [http://alsa.opensrc.org/index.php/Amidi](http://alsa.opensrc.org/index.php/Amidi)

Greetings,
Michael

---

### Post by mango42 on 2010-03-05
Thanks for the pointer, babarosa but for us non-programmers, the --help function can be very confusing. For instance, issuing **amidi -h** shows the following:-

```
-h, --help             this help
-V, --version          print current version
-l, --list-devices     list all hardware ports
-L, --list-rawmidis    list all RawMIDI definitions
-p, --port=name        select port by name
-s, --send=file        send the contents of a (.syx) file
-r, --receive=file     write received data into a file
-S, --send-hex="..."   send hexadecimal bytes
-d, --dump             print received data as hexadecimal bytes
-t, --timeout=seconds  exits when no data has been received
                       for the specified duration
-a, --active-sensing   don't ignore active sensing bytes

```

so where it says -p it also says --port=name and -r shows --receive=file - hmm - there's something of a disconnect between coders and users here - **man** files are quite impenetrable, imo ;-)

Thanks also for the link - that should set me on the right 'path'...

---

### Post by AutoStatic on 2010-03-05
> **mango42 said:**
> so where it says -p it also says --port=name and -r shows --receive=file - hmm - there's something of a disconnect between coders and users here - **man** files are quite impenetrable, imo ;-)There's a difference between short form options and long form options for CLI commands. In general short form options take no equal sign and are preceded by a single dash, long form options are followed by an equal sign and are preceded by two dashes.

> Since Wget uses GNU getopt to process command-line arguments, every option has a long form along with the short one.  Long options are more convenient to remember, but take time to type.  You may freely mix different option styles, or specify options after the command-line arguments. (From the wget man page)

---

### Post by babarosa on 2010-03-05
mango42,

now I am sitting at my machine and can give advice more thoroughly:

1.) send data to your synth

first copy the syx-file into your home directory. 

At the terminal in the home directory your_home@your_computer:~$ enter "amidi -l"

The output looks like
Dir Device    Name 
IO  hw:1,0,0  MidiSport 2x4 MIDI 1 
IO  hw:1,0,1  MidiSport 2x4 MIDI 2 
 O  hw:1,0,2  MidiSport 2x4 MIDI 3 
 O  hw:1,0,3  MidiSport 2x4 MIDI 4 
IO  hw:2,0,0  X50 MIDI 1 
IO  hw:3,0,0  USB Keystation 49e MIDI 1

At the terminal enter "dir", so you can copy and replace the filename into the following command (replace hw:1,0,0 with the proper adress):

amidi -p hw:1,0,0 -s myDump.syx

Hit "enter". If your synth is set up to receive sysex data, it should work fine.

2.) receive data from the synth

amidi -p hw:1,0,0 -r myDump.syx -t 5  (-t 5 is the timeout parameter)

Hit "enter"

Now start the dump from your synth. Be patient, after finishing the dump, the terminal's command line turns back to input mode.

If you want to save these commands, open the file manager (e.g. nautilus) and enter in the home directory "strg+h". Now the hidden files are shown.
Open ".batch_history" with your texteditor (in xubuntu e.g. mousepad). Delete all the commands you do not need, and edit, type and save more often used ones. Leave _one_ blank (generate it by simply hitting "enter") line at the end!
After saving the file "batch_history", you can recall these commands simply by cursering up and down in the terminal.

Good luck,
Michael

---

### Post by mango42 on 2010-03-06
@ AutoStatic - thanks for the fine-grained (and let's face it, organic & evolving) 'arcanery' - I doubt whether I'll ever get a thorough grasp on the CLI approach - been spoilt for too many years GUI-ing, I guess...

@babarosa - that was really kind of you to lay it all out in such a patient and simple fashion. I really appreciate it.

Just a general comment here: How do we get coders and users to meet in a common language? I've noticed that just about every manual and readme is so programmer oriented, they may just as well be written in Sanskrit (yeah, I know!) as far as us musos are concerned. Quite often most of these manuals are dedicated to describing how to compile the code, which libs have been used and how they all tie together (acronyms abound!) but when it comes to describing what the application actually **does**, how it does it and how the user is supposed to interact with it, there's often precious little useful info and that's often largely out of date, anyway.

Conundrum central. If reasonably high IQ users can't get a handle on how an app performs, how can we contribute to making the manuals better?

---

### Post by AutoStatic on 2010-03-06
> **mango42 said:**
> Just a general comment here: How do we get coders and users to meet in a common language?By joining the [Linux Audio mailinglists]("http://lists.linuxaudio.org/listinfo/"), those are the ultimate lists when it comes to interaction between coders and users. 

> **mango42 said:**
> I've noticed that just about every manual and readme is so programmer oriented, they may just as well be written in Sanskrit (yeah, I know!) as far as us musos are concerned. Quite often most of these manuals are dedicated to describing how to compile the code, which libs have been used and how they all tie together (acronyms abound!) but when it comes to describing what the application actually **does**, how it does it and how the user is supposed to interact with it, there's often precious little useful info and that's often largely out of date, anyway.That is because the programmer of a specific app created that app because he/she had a need for it. So the programmer knows how to use the app, simply because he/she wrote it. So there's no need for a howto on the actual functionality of the program. If there is a need for such a howto for those who need it then it is up to those users to come up with such a howto. That's how communities should work IMO. The devs/coders/programmers create the apps, the users document the apps.

> **mango42 said:**
> If reasonably high IQ users can't get a handle on how an app performs, how can we contribute to making the manuals better?By talking about it in forums and on mailinglists. By asking more experienced users on how they do it. By blogging about it or putting screencasts on display. And then adding all this info to existing documentation or by creating it.

---

### Post by prokoudine on 2010-03-06
> **mango42 said:**
> Just a general comment here: How do we get coders and users to meet in a common language? I've noticed that just about every manual and readme is so programmer oriented, they may just as well be written in Sanskrit (yeah, I know!) as far as us musos are concerned.

As someone with years of experience of writing documentation for money I can tell you that programmers rarely write good user oriented documentation. This is simply not their job.

And by the way it is quite common to improve applications after very sensible yet penetrating questions from people who write user guides :)

> Conundrum central. If reasonably high IQ users can't get a handle on how an app performs, how can we contribute to making the manuals better?

By asking developers sensible questions and (re)writing manuals. It always worked for me :)

---

### Post by mango42 on 2010-03-07
Interesting responses - thank you.

I have peered into the mailing lists (Old Nabble?) but never posted there. The huge and proliferating but often dated Wikis could devour my entire day, 24/7. This is the only forum I feel comfortable posting on, mostly because I haven't had my head bitten off... yet! ;-)

I suppose the bottom line is 'do I want to devote sufficient effort to use this OS to make music or do I want to help improve the programs that would allow me to make music on this OS?'

As I said - conundrum central... yet it is very heartening to see more and more studios running UbuntuStudio professionally.

Tenacity rules? :guitar:

---

### Post by AutoStatic on 2010-03-07
> **mango42 said:**
> I suppose the bottom line is 'do I want to devote sufficient effort to use this OS to make music or do I want to help improve the programs that would allow me to make music on this OS?'It's not really an 'or', you should find yourself some sort of balance between those two points of view. By devoting effort you will always come across bugs, lack of functionality, design flaws, all kinds of deficiencies. What do you do then? Work around them, ditch the application or do you report it? By reporting it you're already helping to improve the software and giving something back to the community. Because even if GNU/Linux is freely available, it doesn't mean it's free as in beer. Personally I almost take it as an obligation to give back as much as possible (bugreports, donations, hanging around on this forum and on mailinglists, I recently picked up packaging) as long as it doesn't devour all my precious time I want to dedicate to making music.

---

