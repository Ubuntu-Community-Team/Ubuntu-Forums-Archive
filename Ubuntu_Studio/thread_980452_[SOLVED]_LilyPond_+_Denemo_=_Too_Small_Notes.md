---
title: "[SOLVED] LilyPond + Denemo = Too Small Notes?"
date: 2008-11-12
forum: Ubuntu Studio
---

### Post by Tamalin on 2008-11-12
Hey,
Whenever I write a piece in denemo (With Lilypond), and export it as a PDF, the notes are way too small to read.  Is there a way to make them bigger, even with the title, composer, copywright, etc?

---

### Post by Stochastic on 2008-11-12
I don't work with Denemo, but when you have it in Lilypond format you can simply look for or add this line to your score:
```
 #(set-global-staff-size 16)
```
and change that variable to be as big/small as you desire.

---

### Post by paulmerchant on 2008-11-13
If you go to Edit | Score Properties, you can change the font size and the spacing and line height of the staffs.

---

### Post by Tamalin on 2008-11-13
Ok, thanks, we'll see where this goes!

---

### Post by Tamalin on 2008-11-13
Unfortunatly, by increasing the measure size, I made all my notes smaller!  So then I tried the opposite, and decreased measure size, and I got smaller notes again...  Can anyone help me out on this?  Increasing the font size had no effect.
Thanks!

---

### Post by paulmerchant on 2008-11-13
Have you changed the line height of the staffs? I didn't like the default note sizes either, but after a few tweaks with those settings, I was able to make Denemo work well for me. I'm not on my Ubuntu right now or I would be more specific.

[Edit: I just tried it. You have to make dramatic tweaks to the line heights and measure widths to even see a difference. For example, if you change line hight to 200 and measure width to 320, doubling the defaults, you should see a good change in the note size on your scores.]

---

### Post by Tamalin on 2008-11-14
Thank you for the help, but when I open Denemo and choose Edit->Score Properties, I don't see a line height option... I just see measure width and staff spacing.  I am under the Layout tab.

---

### Post by Stochastic on 2008-11-15
When you save a file in Denemo is it saved as a .ly file?  If it is, open it in a text editor and follow my post above.  This is the **EXACT** command you need.

---

### Post by Tamalin on 2008-11-15
No, when I save a file, it is not saved as a .ly file.  It is saved as a .denemo file.  If I double click one, it starts the Archive Manager, but gives me an error.  Is it supposed to save a .ly file?  Maybe I should re-install it...

---

### Post by paulmerchant on 2008-11-15
When I said line height, I meant the "staff spacing" setting. Sorry about that. If you go to Edit | Score properties from the main menu and then click the layout tab, you can double both of those settings (or experiment with them) to have much larger score and note sizes.

Some of your confusion might be coming from the fact that Denemo still has quite a few unfinished edges. For example, those settings don't appear to be saved in the .denemo files and need to be set each time you open a file and want to export it to PDF. You should get a decently large score size, however, if you make big enough adjustments to those two settings.

By the way, Denemo appears to have its own binary format for saved files that isn't directly compatible with Lilypond.

---

### Post by Stochastic on 2008-11-15
Weird, I don't know why it has its own binary format, after all it's just a GUI frontend to lilypond and depends on lilypond for all the engraving/exporting.  Is it possible to export to lilypond format, add the global-staff-size line, then import it back into denemo?

---

### Post by paulmerchant on 2008-11-15
I never noticed the option before, but when you save files with Denemo, you can select the Lilypond format. That's good to know.

And I just read in the Save As dialog that the .denemo file type is XML. They don't open in text editors, though. I tried a while back to fix a bug in one of my scores. They must be a compressed XML file or something.

---

### Post by Tamalin on 2008-11-17
Ok, Thank You!  I'm glad my download isn't broken. :)

---

### Post by Tamalin on 2008-11-18
I just tried doubling everything to the values you suggested, but It didn't make any difference when I exported as a PDF.  The notes were just as small, if not smaller, than they were before.  I'm just not sure how to fix this issue...

---

### Post by Stochastic on 2008-11-18
Tamalin, please try these steps:
1. Choose Save As, then in the format menu select Lilypond format (.ly) then click save
2. Open the newly created filename.ly file into a text editor and inside a curly braced section { } with note names that look like { a'4 b''8-. e16 d16 } etc... add the following line ```
 #(set-global-staff-size 18)
```
3. Save the file with the same filename
4. this step can be done two different ways:
    - open a terminal, navigate to the desired folder and execute this command ```
lilypond filename.ly
```
    - open Denemo choose file-open, select the filename.ly file, then click okay, then export the file to pdf

5. If the notes are too big/small then reopen the text file and adjust the number in that new bit of code, then repeat steps 3 & 4

Does this work for you?

---

### Post by Tamalin on 2008-11-19
Thank you, but no, it didn't work.  When I tried to use lilypond to compile the .ly file, I recieved only errors.  Apparently Denemo deosn't make .ly files perfectly.  Also, I cannot just 'open' or import a .ly file in Denemo...  I'm not sure why I can save as a .ly file, but not open one...  The errors from the lilypond compilation are as follows:

GNU LilyPond 2.10.33
Processing `BassDuet.ly'
Parsing...
BassDuet.ly:105:16: error: syntax error, unexpected \tempo
        
                \tempo 4 = 60
Interpreting music... [8][16]
BassDuet.ly:54:18: warning: barcheck failed at: 3/4
    g8 g r4 r 
                  |
[24]
Preprocessing graphical objects...
Interpreting music... 
BassDuet.ly:54:18: warning: barcheck failed at: 3/4
    g8 g r4 r 
                  |
MIDI output to `BassDuet.midi'...
Layout output to `BassDuet.ps'...
Converting to `BassDuet.pdf'...
error: failed files: "BassDuet.ly"

---

### Post by Stochastic on 2008-11-19
Would you mind posting the .ly file as an attachment, or uploading it somewhere.  I could look at it to see where the errors are stemming from (looks like it should be an r2 rather than an r to complete the bar if it's 4/4 time).

I still contend that learning lilypond directly is the best method for notating music in Linux at the moment (though that's just my opinion).

---

### Post by Tamalin on 2008-11-20
Ok, let's try out the attachment mechanism here...
I have attached the file in a .ly file.
Maybe I should join the Denemo project? :)
Do you know where I can find a good Lilypond tutorial...  Thanks!

---

### Post by paulmerchant on 2008-11-20
Sorry Denemo isn't working for you, Tamalin. I've only made a couple of small scores and while Denemo feels a little unfinished, it ended up working quite well, including allowing me to increase the size of the scores quite easily.

I wonder if I somehow have a slightly updated dependency or Denemo package. I thought I installed it through the standard repositories.

---

### Post by Stochastic on 2008-11-20
Okay, so it looks like there were only two bugs that I saw in the file.

1) On line 54 of the original file```
g8 g r4 r |
``` is two eighth notes followed by two quarter rests (followed by an unnecessary manual barline - lilypond will put the barlines in if you don't write them).  This does not fill up the 4/4 bar, so I've changed it to ```
g8 g r4 r2 |
``` to fill the bar.  You could also change that bar to a 3/4 bar if that's what you were intending.

2) On line 105 of the original file```
\tempo 4 = 60
``` is totally right! But it's in the completely wrong spot.  It should be on line 30 or so within the music section of the file, not the midi file call.  This was the error in the file that stopped Lilypond from finishing.

I've attached the altered .ly file in tar.gz format, but it'd be better if you tried to make these edits yourself before downloading the attachment (it'll help you learn lilypond).

As for a good tutorial, if you have lilypond installed on your computer, then you should bookmark this link [file:///usr/share/doc/lilypond/html/Documentation/index.html](file:///usr/share/doc/lilypond/html/Documentation/index.html) as it is really nice to be able to use your browser's find function to search through the 'one big page' files.
A warning though, Lilypond is a tough language to jump straight into from a GUI, especially if you do complex music, be prepared to spend some time learning the ropes.

Hope this helps.

---

### Post by Tamalin on 2008-11-21
Wow! Thank, You, it worked.  I am glad I can now fix this problem.
Thank You also for the tutorial reference, as it may be very useful in future ventures.  I might report this as a bug to Denemo, and I might just take a look at the source code if it's Java or C.  I'm glad this problem is resolved...  If I were running Windows, I probably would have never figured it out. :)

---

### Post by rshann on 2009-01-17
Apologies for the confusing options in Staff Properties and Score Properties. The one you want is in Score Properties->layout->font size.
If you set the font size larger everthing will go larger.
The settings about spacing etc in Staff Properties refer to the display only, not to the LilyPond generated.
There is now a LilyPond window inside Denemo, where you can edit the LilyPond output for more specialized uses. Loading LilyPond is just for emergency purposes, it usually takes some hacking.
Any other problems - don't hesitate to ask on Denemo.org
Richard Shann

---

